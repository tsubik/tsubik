---
layout : layout
title : Tomasz Subik Mega Master software/web developer ASP.NET MVC Developer
---
<div>

<div id="two-column-wrap">
                <section id="infoPhoto">
            <img src="images/photo.jpg" />
        </section>
        <section id="infoContent">
            <section id="infoSection">
            <table>
                <tr>
                    <td><span id="implement"> =></span></td>
                    <td><span class="bracket"> {</span></td>
                    <td>
                        <div id="infoSectionMeDesc">
                            <p>
                                I am open-minded software developer loving to create useful web apps. Currently working using C#, asp.net mvc, jQuery.
                                Having strong SQL, T-SQl background. Experimenting with NancyFX, simple ORM mappers like Dapper, Simple.Data and bunch of other cool stuff.
           
                            </p>
                            <p>
                                On the other hand I am sport addicted person. Ice and inline skater, snow and ski lover, free time jogger.
                            </p>
                            <p class="mailme">
                                <span class="leftCol">Mail me</span>tsubik@gmail.com <br />
                                <span class="leftCol">Find me on</span><a href="http://www.github.com/jaymz85"><img src="images/github-icon.png" /></a><a href="http://www.goldenline.pl/tomasz-subik"><img src="images/goldenline-icon.png" /></a>
                            </p>
                        </div>
                    </td>
                    <td><span class="bracket"> }</span></td>
                </tr>
            </table>
            </section>
        </section>
    </div>
	<div style="clear:both;"></div>
	{% for post in site.posts  limit:1 %}
        <section class="blog-posts">
            <article>
                <header class="post-header">
                    <h1 class="post-title">
                        {{post.title}}
                    </h1>
                    <p>
                        <time datetime="2012-07-30">{{ post.date | date: "%e %B, %Y"  }}</time>
                    </p>
                </header>
                <div class="post-content">
                    {{post.content}}
                </div>
                <div class="post-readmore">
                    <a href="{{post.url}}">Read more...</a>
                </div>
            </article>
        </section>
   {% endfor %}
   </div> 