
# Table of Contents

1.  [An Emacs Course](#orgabecb1e)
    1.  [Introduction](#org6af2d8e)
    2.  [Setup](#org3c238b3)
        1.  [Install the configuration and the course](#org88b343b)
        2.  [Start Emacs and let it install the required Emacs packages](#org904d461)
    3.  [Start the course](#org32dcc04)
        1.  [a short word on the notation of key commands](#org17e3e21)
        2.  [Activate a theme for better readability](#org6370a5f)
        3.  [Starting the lessons](#org7a114e6)
    4.  [Planning of learning stages](#org45b7923)



<a id="orgabecb1e"></a>

# An Emacs Course


<a id="org6af2d8e"></a>

## Introduction

I had used Emacs for many years in its most simple way - just as a
programming editor, just using the minimal set of exotic
commands. But when I discovered around 2009 what Emacs really is -
one of the most flexible and well documented programming
environments that happens to be a very good editor as well, I was
blown away.

Org mode was a revelation - the dream of every scientist (physical
chemistry was my original profession). A notebook where you could
write easy marked up text, math, you could calculate, and as a
programmer you could use all your programming languages inside of
the documents and produce graphics inline - too good to be
true. And then it is one of the best task management systems as
well. I fell in love, learned lisp - enjoined its different feel from
the C and scripting languages I knew - something that reminded me of
the joy of playing with the HP Scientific Calculators many year ago.

For a long time I entertained the hope of passing on the
know-how. But it's not so easy, since the thing which makes Emacs so
great and efficient - its staggering flexibility - also makes it
tough to teach. Most long time users end up with configurations that
fit them like a glove. But other users will be very opinionated in regards
to the packages and optimizations that are used. There's a good number
of excellent meta-distributions around, like [Spacemacs](https://www.spacemacs.org/) or [Doom](https://github.com/hlissner/doom-emacs). They
are great and will fit many users. I myself always stayed with my hand-written
config that I constantly adapted to more modern styles (which prevented
me from ever declaring the dreaded [Dot Emacs Bankruptcy](https://www.emacswiki.org/emacs/DotEmacsBankruptcy)).

I now decided to make a first test run with a course that is based on
basic configuration of Emacs. I will start with an initial configuration
that already has a number of nice packages that will wet the appetite.
But the idea is not that learners shall adopt these exact configurations.
They should learn how the configuration works and how they can adapt
it. So, they by themselves will be able to make an informed decision about
whether they want to adopt one of the meta distributions, change the
present one, or just develop their own.

My big thanks goes to the whole Emacs community. One of the most
welcoming and helpful communities I had the pleasure to work with.
So many people have contributed to this products and I feel indebted
to all of them.


<a id="org3c238b3"></a>

## Setup


<a id="org88b343b"></a>

### Install the configuration and the course

The Emacs configuration for the course you can find at
<https://github.com/dfeich/emacs-course-and-config>. 
It is best that you fork that repository and then clone your
forked copy to your (or a test user's) account's `~/emacs.d` directory on your
machine.

    git clone git@github.com:dfeich/emacs-course-and-config.git ~/.emacs.d
    
    # or if you made a fork
    
    git clone git@github.com:<YOUR-GITNAME>/emacs-course-and-config.git ~/.emacs.d

This repository contains the course in the form of Org mode task files.
It should be checked out into the `~/Documents/orgcourse` folder of your account.
The Emacs configuration for the course contains settings that expect to
find the files under that location.

    git clone git@github.com:dfeich/emacs-course.git ~/Documents/orgcourse

If you check out to another location, you need to adapt the
definition in the Emacs configuration.

When you start Emacs with the new configuration for the first time, it
will download all the missing packages from GNU, MELPA, and Org. This
may take some minutes.

I use Emacs version 26.3 and Org version 9.x for this course.


<a id="org904d461"></a>

### Start Emacs and let it install the required Emacs packages

When you start Emacs with the new configuration, it will download
the packages that are defined in the config. It may also have to
compile some extensions and pull in some OS packages (e.g. for the
PDF integration).

Packages are pulled down from the [GNU ELPA](https://elpa.gnu.org/), [MELPA](https://melpa.org/#/), and [Org](https://orgmode.org/)
repositories. GNU ELPA has recently changed its gpg keys, so you
may need to run the following command in order to update your
gpg security configuration (q.v. [this nice article](https://metaredux.com/posts/2019/12/09/dealing-with-expired-elpa-gpg-keys.html))

    gpg --homedir ~/.emacs.d/elpa/gnupg --receive-keys 066DAFCB81E42C40

If Emacs stops with an error message, it does not necessarily
mean that there is a critical problem. Close Emacs either using your
mouse pointer or hit the `CTRL-x CTRL-c` key combination. Launch it
again and look whether it is able to progress further. Since some
downloaded packages are replacing older versions of existing
packages, it can sometimes happen that depending on your current
config, Emacs ends up in a state where the old package and the new
package conflict. Updating packages like we do it here, actually
means that we are **live-patching Emacs**. Usually Emacs deals
admirably well with this, since the largest part of its
functionality is written in LISP. But exchanging cogwheels while
the motor is running can sometimes lead to problems (we will learn
in some later lesson about package management how to avoid this).

If it fails repeatedly without progressing further then please
file an issue in this tracker, and I will try to help.


<a id="org32dcc04"></a>

## Start the course

Once you have everything installed, start the first stage by typing

    emacs ~/Documents/orgcourse/agenda/course01-basics.org


<a id="org17e3e21"></a>

### a short word on the notation of key commands

Emacs is operated through control key combinations and all Emacs
documentation uses the following important notation convention for
the keystrokes:

-   **"C-f":** this means hit the `CTRL` key together with the `f` key. The leading
    key in front of the dash always refers to `CTRL`
-   **"M-f":** M refers to the `META` key, which on Linux/MS-Windows is
    the `ALT` key (On Macs this can be the `Option` or `Command`
    key). So, `M-f` means press the `ALT` key together with the `f` key
-   **"S-g":** `S` is short for the `SHIFT` key, so this means press `SHIFT` and `g`
    together
-   **"M-S-;":** this means press the `META`, `SHIFT`, and `;` keys together.

Often commands consist of a key combination like

-   **"C-h e":** first press `CTRL` + `h`, then press `e`
-   **"C-c C-c":** press `CTRL` + `c` twice


<a id="org6370a5f"></a>

### Activate a theme for better readability

The file you are viewing is written in Org mode which is a
sophisticated markup mode. Here, and also in other parts of Emacs
it is immensely helpful to use a theme that also visually marks up
the different text elements. The Emacs configuration for this
course has installed [Fabrice Niessen's Leuven theme](https://github.com/fniessen/emacs-leuven-theme), which is my
own preferred light theme (you can naturally install others later).

**The theme still needs to be activated.** Use your mouse to select
within the `Options` menu on the top of your Emacs window:
`Customize Emacs -> Custom Themes`. On the displayed page with themes,
select the `leuven` theme (not `leuven-dark`) and use the `Save Theme Settings`
button to save the configuration. Then you press `q` to quit this buffer,
and you will be back in our course's first lessons file.


<a id="org7a114e6"></a>

### Starting the lessons

You should now see an Emacs session that looks like this

![img](README-att/course-start.png)

Navigate to the first headline (headlines are marked by one or multiple
leading stars) and unfold it by using the `<TAB>` key while you are on it.
You can press `<TAB>` multiple times, and it will cycle between the different
folding states.

When you open the **Course basics** you will see the following and you are
ready to go

![img](README-att/course-start2.png)


<a id="org45b7923"></a>

## Planning of learning stages

This is what I am planning to cover. Let's see whether I'll be able to
pull through&#x2026;

The sequence beyond step 1 is up to change&#x2026; I will teach a small
number of work colleagues in this first round. I'll adapt to the
feedback I will get. All of this will be hands-on with prepared
documents for the lessons. The configuration will grow with the
material covered in the lessons - and I may leave holes for this
first round, since the coworkers know some items already.

I will try to teach the most important standard Emacs commands, but
a lot of material will focus on **using the benefits of modern packages**.
The most basic standard commands are important if one ever finds oneself
having to use an unconfigured Emacs. But the real convenience and power
is attained through the add-ons that the community has created over
the years.

This is a **work in progress.** The parts which I have already covered, I mark
by filled checkboxes.

1.  Basic Emacs and Org mode
    -   this is a big first stage, but I think that Org mode must be introduced
        early, because it is one of the principal features that immediately
        offers big benefits to new users
    -   basic editor features
        -   [X] file loading, saving, save as
        -   [X] searching for strings and regexps
    -   file management
        -   [X] efficient file navigation with helm and ido
        -   [ ] dired file manager - basic commands
    -   [X] org mode as a basic task manager (org agenda, basic org file features)
    -   [X] executing Emacs commands
        -   [X] using smex or helm to more easily execute commands
    -   [ ] Emacs package management
    -   [X] how to use the info and help systems
    -   [ ] minimal Emacs lisp knowledge, just enough to understand the config
        in a rudimentary way and lose the fear of parentheses
2.  Emacs for higher productivity, programming and system management
    -   [ ] Emacs daemon
    -   [ ] Magit - is there a better Git interface than this project from Jonas Bernoulli?
    -   [ ] Tramp (a killer feature for users working on remote hosts. Loved by
        system administrators and developers)
    -   [ ] Org capture - create tasks and back-links from everywhere
    -   [ ] Emacs Macros
    -   [ ] do inline calculations with Calc
    -   [ ] dired revisited
    -   [ ] shell command execution from Emacs
    -   [ ] a look at some of the programming modes
    -   [ ] lsp-mode (a modern IDE interface in Emacs)
    -   [ ] linting (Syntax checking with flycheck)
    -   [ ] gpg for encrypting files
3.  Authoring Latex, HTML, and other documents with Org mode
    -   [ ] write scientific documents containing math, preview the math
    -   [ ] include graphics and screenshots
    -   [ ] simple first steps with Org Babel to execute code and
        create graphics
4.  Org Babel for real
5.  Fast Presentations with Latex beamer through Org
6.  Integrating with your browser
    -   [ ] Use Emacs to edit forms in browsers like Firefox or Chrome
        (through the daemon)
    -   [ ] org-protocol: transfer information from the browser to Emacs,
        e.g. mark some text in the browser and get it into Emacs, or
        convert a web page to org mode and find it ready in your buffer!
7.  Emacs and email
    -   [ ] mu4e and mbsync to manage email
    -   [ ] integrate email with org mode task management, making
        efficient use of org capture and email links in workflows.
8.  Emacs for science
    -   [ ] helm-bibtex
    -   [ ] org-ref
    -   [ ] org-babel
    -   [ ] org-noter and PDF management
    -   [ ] jupyter (maybe)

