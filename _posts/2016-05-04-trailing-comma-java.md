---
layout: post
title: Trailing Commas in Java Arrays and Enums
---

A lot of Java developers might not know that trailing commas are allowed in Java arrays (see [JLS Array Initializers][jls-array-initializer]). That means you can do something like this

{% highlight java %}
String[] dinosInJurassic =  {
  "Archaeopteryx",
  "Diplodocus",
  "Plesiosaurus",
  "Triceratops", // ← trailing comma
};
{% endhighlight %}

... or even this, if you want ([ref][so-array-syntax]):

{% highlight java %}
int i[][] = { {,}, {,}, {,}, }
{% endhighlight %}

I have to admit that the first snippet is the better example for the remaining text.

# Benefits

Let let me first explain why this is a good thing. There are two main benefits according to [Nik Graf][nik-dangling-commas], and although he wrote about JavaScript/ECMAScript, I think they are perfectly applicable to Java:

1. Clean diffs
2. Easy code manipulation

If this is not immediately clear, please read [his article][nik-dangling-commas]. It's a good read with visual examples. The gist: code changes and you want to only see the relevant changes in your diff and don't want to change more than necessary.

In other words and back to example 1 above: If you find another dinosaur that lived in Jurassic, or find out one of them did not actually live there (yes, it's the Triceratops), you just add or remove a line.

# Automated Checks

Nik alsorecommends enforcing this style with linting. In the Java world a lot of people use [Checkstyle][checkstyle-sourceforge] to make sure that code adheres to their standards, and of course there is a rule for this: [`ArrayTrailingComma`][checkstyle-arraytrailingcomma].

The following is a minimal checkstyle configuration using this setting:

{% highlight xml %}
<module name="Checker">
  <module name="TreeWalker">
    <module name="ArrayTrailingComma" />
  </module>
</module>
{% endhighlight %}

The good thing about this is that it checks multi-line array definitions, so something like the second example is not enforced. I included this snippet, because I don't use Checkstyle that much, but wanted to find out, whether it works correctly. There is even more usable stuff around this example [here][github-trailing-commas].

# Is There More?

The title gave it away: You can also use these trailing commas in `enum` definitions (see [JLS Enum Constants][jls-enum-constants]). The code I work with usually contains more enums than multi-line array definitions and I think this is not too uncommon.

I tend to write enums this way:

{% highlight java %}
enum MovieTypes {
  GOOD,
  BAD,
  UGLY,
  ;
}
{% endhighlight %}

Same benefits as above, but unfortunately I cannot enforce this using Checkstyle, because I haven't found the corresponding rule yet.

[checkstyle-arraytrailingcomma]: http://checkstyle.sourceforge.net/config_coding.html#ArrayTrailingComma
[checkstyle-sourceforge]: http://checkstyle.sourceforge.net/
[github-trailing-commas]: https://github.com/kariem/trailing-commas
[jls-array-initializer]: http://docs.oracle.com/javase/specs/jls/se8/html/jls-10.html#jls-10.6 "Java Language Specification - 10.6: Array Initializers"
[jls-enum-constants]: http://docs.oracle.com/javase/specs/jls/se8/html/jls-8.html#jls-8.9.1 "Java Language Specification - 8.9.1: Enum Constants"
[nik-dangling-commas]: https://medium.com/@nikgraf/why-you-should-enforce-dangling-commas-for-multiline-statements-d034c98e36f8 "Why you should enforce Dangling Commas for Multiline Statements"
[so-array-syntax]: http://stackoverflow.com/q/11621917/12039
