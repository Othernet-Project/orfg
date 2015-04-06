=============================
Outernet RSS format guidlines
=============================

The Outernet RSS format guidelines (ORFOG) is a set of guidelines for content
publishers. Its aim is to make conversion of content for publication on
Outernet easier and more reliable. ORFOG builds on `RSS 2.0 specification`_,
and familiarity with that standard is assumed.

While we use the same set of elements as RSS 2.0 specification, some elements
have a slightly different meaning/usage. In this document, we will cover the
semantic differences between RSS 2.0 specification and ORFOG guidelines, and
briefly touch on content authoring.

In addition to elements required by the RSS 2.0 specification, elements
discussed below are all **required** by ORFOG.

Status
======

This document is an **EARLY DRAFT**.

Last modified: 2015 Apr 7

(c)2015 Outernet Inc.

Channel elements
================

title
-----

This element commonly contains the channel title. In ORFOG, this element
shoudld contain the **publisher name**.

Example::

    <title>Detsche Welle</title>

Title is used to display attribution information to the user. It may be used in
expressions such as "by Detsche Welle" or "from Detsche Welle".

link
----

This element should contains the channel URL as used on the web. If the content
is not publicly available on the Internet, ``outernet://`` scheme may be used
instead of ``http[s]://``.::

    <link>http://www.dw.de/</link>

Although the value is a full URL of the channel, only the domain is used
directly in the client software. The domain may be used to present the channel
content to the users when they use the domain name in their browsers' address
bars.

language
--------

In ORFOG this element should always be included, even though it is not required
by RSS 2.0 specification.

copyright
---------

The value of this element is used to present licensing information to the user.
It should contain one of the following values:

* ``ARL`` (All rights reserved)
* ``ON`` (Other non-free license)
* ``CC-BY`` (Creative Commons Attribution)
* ``CC-BY-ND`` (Creative Commons Attribution-NoDerivs)
* ``CC-BY-NC`` (Creative Commons Attribution-NonCommercial)
* ``CC-BY-ND-NC`` (Creative Commons Attribution-NonCommercial-NoDerivs)
* ``CC-BY-SA`` (Creative Commons Attribution-ShareAlike)
* ``CC-BY-NC-SA`` (Creative Commons Attribution-NonCommercial-ShareAlike)
* ``GFDL`` (GNU Free Documentation License)
* ``OPL`` (Open Publication License)
* ``OCL`` (Open Content License)
* ``ADL`` (Against DRM License)
* ``FAL`` (Free Art License)
* ``PD`` (Public Domain)
* ``OF`` (Other free license)

These values are case-insensitive.

image
-----

The image sub-element may be included with standard semantics. It is currently
not used, but maybe be used in future to display a channel thumbnail in client
software.

Item elements
=============

The ``title`` element is not required and will not be used. The only required
elements are ``description`` and ``pubDate``.

description
-----------

This element is required, and should contain the full HTML markup of a page.
All external assets such as images, CSS, and JavaScript should be referenced
using absolute URLs.  Note that enclosures will not be parsed.

See `Content authoring considerations`_ section for further guidelines
regarding content.

Content authoring considerations
================================

Titles should be short and rich
-------------------------------

Titles should be concise and contain enough relevant keywords to facilitate
easier searching.

Keywords meta tags is allowed
-----------------------------

The content may include the ``keywords`` meta tag. The keywords should be a
case-insensitive list of comma-separated keywords. For example::

    <meta name="keywords" content="medical,surgery,hear,diseases">

They will be used for indexing, along with the title. Note that keywords should
be in the same language as the content itself.

Keep format meta tag
--------------------

The content may include a non-standard ``keep-formatting`` meta tag. If this
tag is encountered, Outernet software should treat the page as fully formatted
and not apply internal stylesheet designed for unformatted pages.

Keep in mind that shipping your own styling with the page does increase the
bandwidth consumption.

HTML markup
-----------

Content published on Outernet is often transmitted through low-bandwidth
channels such as DVB-S and shortwave. Because of this, it is recommended that
content is concise and free of superfluous markup that is used for purely
decorative purposes. 

An example of markup that can be commonly found on Internet today may look like
this::

    <div class="editor-note expanded" id="ed-note-expandable">
        <div class="inner">
            <div class="inner-wrapper">
                <h2>
                    <span class="editor-note-icon">&nbsp;</span>Editor's notes
                </h2>
                <p>
                    Lorem ipsum...
                </p>
            </div>
        </div>
    </div>

What is essentially useful content from the above code is this::

    <h2>Editor's notes</h2>
    <p>
        Lorem ipsum...
    </p>

As can be seen, significant amounts of markup can be removed to save bandwidth
and allow Outernet users to receive content faster. 

.. RSS 2.0 specification: http://www.rssboard.org/rss-specification

