WORKFLOW
--------
rake new_post["new post"]
rake new_page[super-awesome] # creates /source/super-awesome/index.markdown
rake new_page[super-awesome/page.html] #creates /source/super-awesome/page.html
rake generate
rake preview

BLOGGING
--------
Trying blockquotes
{% blockquote Anonymous%}
he said "i love you" 
i sneezed and said 
"sorry, i'm allergic to bull shit"
{% endblockquote %}

Some code in Java
{% codeblock Very useful snippet - GoodManners.java lang:java %}
public static String sayHola(){
  System.out.println("Hola compadre");
}
{% endcodeblock %}

And now some images
{% img http://127.0.0.1:4000/images/email.png %}