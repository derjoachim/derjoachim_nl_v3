---
layout: post
title: OOP versus procedural programming, the pirates versus ninja way
joomla_id: 27
joomla_url: oop-versus-procedural-programming-the-pirates-versus-ninja-way
date: 2011-07-27 23:00:00.000000000 +02:00
author: Joachim van de Haterd
category: Technical thoughts
tags: [Programming]
---
<p>A few weeks ago, I tried to explain the concepts of Object Oriented Programming versus Procedural Programming to a she-geek. There was a catch: up to a few weeks ago, she know next to nothing from computers. The analogies I used were so bad, that I really want to share them.</p>



<h2> Because they are cool</h2>

<p>Formerly, computer programs were created in a procedural way: a sequence of events was to be called, and when a small piece had to be called again, the entire procedure had to be redone.  OOP works on an entirely different level. Objects are being created and manipulated, and by cleverly dividing them among classes, they can be manipulated in cunning ways. To clarify this to aforementioned she-geek, I dug up an age-old rivalry, being ninja's versus pirates.  Why? Simply because both are cool. Arr!</p>

<h2>Procedural pseudo-PHP </h2>

<p>Let's say that Pirates and Ninjas both have a very small set of actions (be instantiated, equip something, speak, fight, and be killed again). In pseudo code, you could do it like this.</p>

<pre>// Instantiation<br />$x = Ninja();<br />$y = Pirate();<br /><br />// Speakingfunction  say_yes($person) {<br />  if(typeof($person) == "Ninja') {<br />    echo "Hai!";<br />  } else if (typeof($person) == "Pirate") {<br />    echo "Arr!";<br />  } <br />}<br /><br />// Wield something, dependent on class <br />function equip($person, $weapon) {<br />  if(typeof($person) == "Pirate") { <br />    $person.wearsCutlass = true; <br />  } else if(typeof($person) == "Ninja") {<br />    $person.wearsKatana = true;<br />  }<br />}// Kill them.<br /> <br />function killNinja($person) {<br />  if(typeof($person) == "Ninja") {$person = null; } <br />}<br />function killPirate($person) {<br />  if(typeof($person) == "Pirate") {$person = null; }<br />}

</pre>

<p>There's a few big flaws in this code. A lot of it is being repeated, and a lot of unnecessary checks are being made. There are two kill-functions, while essentially, killing a person happens in roughly the same way for both pirates and ninjas. A lot of unnecessary checks are made. A pirate cannot use a katana, using this code, but the way to verify this, is quite primitive.</p>

<h2>Pirates versus Ninjas, the OOP way</h2>

<p>Pirates and ninjas have a lot in common, but there are differences as well. They can both speak, they can both be killed, but a ninja cannot wield a cutlass, whereas a pirate would not recognize the buisness end of a katana. Let us sort these specifications and transform these into more object-oriented code:</p>

<pre>class person {<br />  function _initialize() {<br />    $x.isAlive = true;<br />  }<br />  function kill() {<br />    $x.isAlive = false;<br />   }<br />  }<br />  // A pirate is a type of person <br />  class pirate extends person { <br />    $x.wield_cutlass = false; <br />    function _initialize() {<br />      parent::initialize();<br />    } <br />    function destruct() {<br />     parent::destruct();<br />   } <br />    function say_yes() {<br />      echo 'arrr!!!';<br />    }<br />    function equip() {<br />      $x.wields_cutlass = true;<br />    } <br />   }<br />  // Ninjas are a different kind of person<br />  class ninja () {<br />    $x.wields_katana = false; <br />

    function _initialize() {parent::initialize();}  function destruct() {<br />

    parent::destruct();<br />

  }<br />  function say_yes() {<br />

  echo 'Hai';<br />

}<br />

function equip() {<br />

     $x.wields_katana = true;

 }<br />

}<br />

$blackbeard = new pirate(); // and human as well in one fell swoop<br />$hiro = new ninja(); // Again: human<br />$blackbeard.equip(); // He wields a fearsome cutlass now<br />$hiro.equip(); // Now has a badass katana<br />$blackbeard.say_yes(); // "Arrr!"<br />

$hiro.say_yes(); // "Hai"<br />

$blackbeard.destruct();<br />

$hiro.destruct();</pre>

<p>As you can see, the code is better structured. The special classes inherit the common traits from person, the special stuff is kept special, and everythisg is as it should be. Furthermore, there is no necessary repetition, thus making it easier to edit common tasks, like say, killing. Instead of having to edit many similar functions for killing stuff, only the kill-function in the person class has to be edited.</p>

<h2>Procedural versus OOP: Who wins? </h2>

<p>Okay, here's a spoiler. Of course, OOP is the way to go. Every programmer knows that the best way to deal with complex data structures is by dividing them in a sensible way. OOP is one such abstraction. The DRY (don't repeat yourself) principle was nicely demonstrated in my pirates versus ninjas sample.</p>

<p>Tomorrow, the lessons will continue. I'm still brooding on a way to pour the MVC paradigm in a Pirates versus Ninjas context. To be continued, hopefully. :)</p>
