# OpenACS Developer Support
This package is part of ]project-open[, an open-source enterprise project management system.

For more information about ]project-open[ please see:
* [Documentation Wiki](http://www.project-open.com/en/)
* [V5.0 Download](https://sourceforge.net/projects/project-open/files/project-open/V5.0/)
* [Installation Instructions](http://www.project-open.com/en/list-installers)

About OpenACS Developer Support:

<p>part of the <a href="http://openacs.org/doc/acs-developer-support/">ArsDigita Community System</a>, by <a href="mailto:jsalz@mit.edu">Jon Salz</a>, taken from <a href="http://openacs.org/doc/acs-developer-support/">http://openacs.org/doc/acs-developer-support/<span class="external"> </span></a>: <p><hr /><ul><li>Admin interface: /www/admin/monitoring/request-info.tcl<li>Procedures: /packages/developer-support-procs.tcl, with support in: <ul><li>/tcl/ad-abstract-url.tcl<li>/tcl/ad-defs.tcl.preload<li>/tcl/ad-security.tcl.preload</ul></ul><h3>The Big Picture </h3><h3>Peeking Under the Hood </h3><p>Our development environment previously consisted largely of Emacs, and <tt>tail -f /web/servername/log/servername-error.log</tt>. Now this has been augmented: <tt>ad_footer</tt> and <tt>ad_admin_footer</tt> now display a link entitled <em>Developer Information</em>. (You can use the <tt>ds_link</tt> procedure to generate the link yourself.) Following the link displays a screenful of information including: <ul><li>The times that the request started and ended, and its duration (with millisecond accuracy).<li>The request parameters (method, url, query, headers, etc.).<li>The output headers, if any.<li>Information about all database queries performed while loading the page, including their respective durations (with millisecond accuracy).</ul><p>In addition, the ClientDebug facility of AOLserver 2 has been re-implemented in the abstract URL system (which serves nearly all non-static pages). If an error occurs while serving a page, a stack trace is printed out. <p>Note that these nifty features pop up only when you are logged in as a site-wide administrator! Revealing this information to anyone else would pose a huge security risk. <h3>Comments </h3><tt>ns_log</tt><tt>ds_comment</tt><blockquote><pre>ds_comment &quot;Foo is $foo&quot;</pre></blockquote><em>Developer Information</em><p>Comments are displayed even if an error occurs in the page! <h3>Enabling It </h3><tt>parameters/yourservername.ini</tt><blockquote><pre>[ns/server/yourservername/acs/developer-support]
; remember information about connections, for developers&#39; benefit?
EnabledP=1
; remember information about every database request?
DatabaseEnabledP=1
; remember information for which client hosts?
EnabledIPs=*
; remember this information for how long? sweep how often? (in seconds)
DataLifetime=900
DataSweepInterval=900</pre></blockquote><h3>How It Works </h3><tt>nsv</tt><tt>ns_db</tt><hr /><address><a href="mailto:jsalz@mit.edu">jsalz@mit.edu</a></address><p>

# Online Reference Documentation

