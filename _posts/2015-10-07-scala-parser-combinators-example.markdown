---
title:  "Parser Combinators Example in Scala"
date:   2015-10-07 10:18:00
description: A simple example of using the scala library for parser combinators to build a useful application.
---

In this post, I'll walk you through building a simple calculator that evaluates nested operations by writing a custom interpreter for it using the 
parser combinator library in scala. For more information on parser combinators, please refer to [this page.](http://www.artima.com/pins1ed/combinator-parsing.html)

You need to have installed `scala` as well as `sbt.` First, create a directory to contain your project. I'm calling it `pc-calculator.`

{% highlight scala %}
mkdir pc-calculator
{% endhighlight %}

Enter the directory.

{% highlight scala %}
cd pc-calculator
{% endhighlight %}

Create the `build.sbt` file.

{% highlight scala %}
touch build.sbt
{% endhighlight %}

Open `built.sbt` and copy the following code into the file.

{% highlight scala %}
name := "parser"

version := "1.0"

scalaVersion := "2.11.4"

libraryDependencies += "org.scala-lang.modules" %% "scala-parser-combinators" % "1.0.4"
{% endhighlight %}

Create a directory called `project` and enter the it.
{% highlight scala %}
mkdir project
cd project
{% endhighlight %}

Create a file called `plugins.sbt` and populate it with the following information.

{% highlight scala %}
touch plugins.sbt
// add the following line to the file.
addSbtPlugin("com.typesafe.sbteclipse" % "sbteclipse-plugin" % "2.5.0")
{% endhighlight %}

Go back to the parent directory.
{% highlight scala %}
cd ../
{% endhighlight %}

Now type `sbt` in the console.
{% highlight scala %}
sbt
{% endhighlight %}

After the dependencies are installed, you will see a `>` sign. Type `eclipse` and this will set up the eclipse project for you. Now import this directory into the 
Scala Eclipse IDE by going to `File --> Import --> Existing Projects into Workspace --> Select directory pc-calculator --> Finish.`

Now comes the actual project. The calculator that we define will be able to parse and evaluate statements such as `(1+2)` and `(1+(1+(3+2))).` We can define the grammar
for our 'language' (informally) as follows:

There are two main constructs that we deal with, `numbers`, and the `operations` to be performed on them. These are our so called terminal symbols. These fundamental
constructs form the complex expression like the ones described above. Now, we establish the notion of an expression as follows. An expression consists of:

* An opening bracket `(` followed by.
* A number or **another nested expression** followed by.
* An operation, `+`, '*', `-` in our example followed by.
* A number or **another nested expression** followed by.
* A closing bracket `).`

This is exactly how we describe our grammar in code. Create a Scala class called `Main` in the imported project.

{% highlight scala %}
import scala.util.parsing.combinator._

  class Calculator extends JavaTokenParsers {
      def number : Parser[Int] = """[0-9]+""".r ^^ (_.toInt)
      
      def operation : Parser[String] = "+" | "*" | "-"
      
      def expr : Parser[Int] =  "(" ~> (number | expr) ~ operation ~ (number | expr) <~ ")" ^^ {
        case resOne ~ "+" ~ resTwo => resOne + resTwo
        case resOne ~ "*" ~ resTwo => resOne * resTwo
        case resOne ~ "-" ~ resTwo => resOne - resTwo
        
       }
  }
  
  object CalculatorTest extends Calculator {
 
  def main(args: Array[String]): Unit = {
    println(parseAll(expr  , args(0)))
  }
 
}

{% endhighlight %}

The code is structured as follows:
* The `Calculator` class extends the `JavaTokenParsers` class to get the common functionality associated with parsers. We then define our grammar.
* The function `number` is just what we described, a regular expression which matches multiple digits from 0 to 9. The triple quotes `"""` and `.r` are just scala
features to convert `[0-9]+` to a regular expression. Now after parsing these symbols, we need to do something with them. That is exactly what the `^^` symbol enables.
The block of code after the `^^` sign is executed after the parse is completed. In this case, we just need to convert whatever we matched to an integer.
* The `operation` function matches **either** a `+`, or a `*` or a `*` sign.
* The `expr` function captures the logic as we described earlier. 

That's all for now. This should prepare you to build a more complicated language for your purposes.












[jekyll-gh]: https://github.com/mojombo/jekyll
[jekyll]:    http://jekyllrb.com
