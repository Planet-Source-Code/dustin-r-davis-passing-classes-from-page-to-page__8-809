<div align="center">

## Passing classes from page to page


</div>

### Description

Ever needed to pass a class and its data from one page to the next? I will show you how.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Dustin R Davis](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/dustin-r-davis.md)
**Level**          |Beginner
**User Rating**    |4.0 (16 globes from 4 users)
**Compatibility**  |PHP 4\.0
**Category**       |[Data Structures](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/data-structures__8-8.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/dustin-r-davis-passing-classes-from-page-to-page__8-809/archive/master.zip)





### Source Code

<P>&nbsp;</P>
<table width="467" border="0" cellspacing="0" cellpadding="0">
 <tr>
  <td bgcolor="#ddddcc"><font color="#000000" size="2" face="Arial, Helvetica, sans-serif"><b>Introduction</b></font></td>
 </tr>
 <tr>
  <td>
   <p><font size="2" face="Arial, Helvetica, sans-serif">The scenario: Lets
    say you have a customer who is buying something. The customer is checking
    out, because he is done shopping. You have setup two pages, one with his
    personal information such as name address etc. and the other with the
    billing information. Since you are so organized and neat, you don't want
    to jumble the page with form fields so you decided to have two separate
    pages.</font></p>
   <p><font size="2" face="Arial, Helvetica, sans-serif">You think to yourself,
    &quot;Wow, that's allot of variables to keep track of!&quot;. You ponder
    how much work this will be and you finally come up with a solution: You
    will use a class to store the information!</font></p>
   <p><font size="2" face="Arial, Helvetica, sans-serif">After designing and
    building a class, you sit back and sip your beer. Unfortunately you cant
    enjoy that sip because you realized that you have no idea how you are
    going to send the information from page one over to page two!</font></p>
   <p><font size="2" face="Arial, Helvetica, sans-serif">Well, I'm going to
    show you how to move your classes and your data that's held in them from
    page to page.</font></p>
  </td>
 </tr>
</table>
<br>
<table width="467" border="0" cellspacing="0" cellpadding="0">
 <tr>
  <td bgcolor="#ddddcc"><font color="#000000" size="2" face="Arial, Helvetica, sans-serif"><b>The
   Class </b></font></td>
 </tr>
 <tr>
  <td align="left" valign="top">
   <p><font face="Arial, Helvetica, sans-serif" size="2">This will held in
    your class.php file. You will need to include this in every page you want
    to access your class and its data.</font></p>
   <blockquote>
    <p><font size="1" face="Verdana, Arial, Helvetica, sans-serif"><b>&lt;?PHP<br>
     class cMyClass {</b></font></p>
    <blockquote>
     <p><b><font size="1" face="Verdana, Arial, Helvetica, sans-serif">var
      $Name;</font></b></p>
     <p><b><font size="1" face="Verdana, Arial, Helvetica, sans-serif"> function
      PrintName() {</font></b></p>
     <blockquote>
      <p><b><font size="1" face="Verdana, Arial, Helvetica, sans-serif">echo
       &quot;Your name is &quot;.$this-&gt;Name;<br>
       return true;</font></b></p>
     </blockquote>
     <p><b><font size="1" face="Verdana, Arial, Helvetica, sans-serif">}</font></b></p>
    </blockquote>
    <p><b><font size="1" face="Verdana, Arial, Helvetica, sans-serif">}<br>
     ?&gt; </font></b></p>
   </blockquote>
  </td>
 </tr>
</table>
<br>
<table width="467" border="0" cellspacing="0" cellpadding="0">
 <tr>
  <td bgcolor="#ddddcc"><font color="#000000" size="2" face="Arial, Helvetica, sans-serif"><b>The
   Input page</b></font></td>
 </tr>
 <tr>
  <td align="left" valign="top">
   <p><font face="Arial, Helvetica, sans-serif" size="2">This page will be
    what you submit your personal information to.</font></p>
   <blockquote>
    <p><font size="1" face="Verdana, Arial, Helvetica, sans-serif"><b>&lt;?PHP<br>
     include(&quot;./class.php&quot;);</b></font></p>
    <p><b><font face="Verdana, Arial, Helvetica, sans-serif" size="1">$myClass
     = new cMyClass;</font></b></p>
    <p><b><font face="Verdana, Arial, Helvetica, sans-serif" size="1">$myClass-&gt;Name
     = $HTTP_POST_VARS[&quot;Name&quot;];</font></b></p>
    <p><b><font face="Verdana, Arial, Helvetica, sans-serif" size="1">...
     //other code you have</font></b><br>
     <br>
     <b><font size="1" face="Verdana, Arial, Helvetica, sans-serif">$_SESSION[&quot;MyClassData&quot;]
     = serialize($myClass); </font></b></p>
    <p><b><font size="1" face="Verdana, Arial, Helvetica, sans-serif">?&gt;
     </font></b></p>
    </blockquote>
  </td>
 </tr>
</table>
<br>
<table width="467" border="0" cellspacing="0" cellpadding="0">
 <tr>
  <td bgcolor="#ddddcc"><font color="#000000" size="2" face="Arial, Helvetica, sans-serif"><b>The
   last page</b></font></td>
 </tr>
 <tr>
  <td align="left" valign="top">
   <p><font face="Arial, Helvetica, sans-serif" size="2">This page will display
    their information to them. The information that was carried over from
    page to page on the site.</font></p>
   <blockquote>
    <p><font size="1" face="Verdana, Arial, Helvetica, sans-serif"><b>&lt;?PHP<br>
     include(&quot;./class.php&quot;);</b></font></p>
    <p><b><font face="Verdana, Arial, Helvetica, sans-serif" size="1">$temp
     = $_SESSION[&quot;MyClassData&quot;];</font></b></p>
    <p><b><font face="Verdana, Arial, Helvetica, sans-serif" size="1">$myClass
     = unserialize($temp);</font></b></p>
    <p><b><font size="1" face="Verdana, Arial, Helvetica, sans-serif">$myClass-&gt;PrintName();</font></b></p>
    <p><b><font size="1" face="Verdana, Arial, Helvetica, sans-serif">?&gt;
     </font></b></p>
   </blockquote>
  </td>
 </tr>
</table>
<br>
<table width="467" border="0" cellspacing="0" cellpadding="0">
 <tr>
  <td bgcolor="#ddddcc"><font color="#000000" size="2" face="Arial, Helvetica, sans-serif"><b>Conclusion</b></font></td>
 </tr>
 <tr>
  <td align="left" valign="top"><font size="2" face="Arial, Helvetica, sans-serif">Unfortunately,
   due to my laziness, I gave a small, crude example. I think you get the point
   though. Once you have designed and built your class, you can save it in
   an include file. Make sure to have this file included in every .php file
   you will be using your class in. In each page you will need to access your
   class data by using <b><font size="1" face="Verdana, Arial, Helvetica, sans-serif">unserialize()</font></b>
   and when you are finished you will need to save it again using <b><font size="1" face="Verdana, Arial, Helvetica, sans-serif">serialize()</font></b>.
   I'm using the session method because I do not have access to write files
   on my server, and it would be too hard to write a file for each person that
   wants to order something. There are too many people. You can look in the
   PHP manual (v10) to figure out how to write them to a file and retrieve
   them from a file.</font></td>
 </tr>
</table>

