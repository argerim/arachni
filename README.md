# Arachni - Web Application Security Scanner Framework
<table>
    <tr>
        <th>Version</th>
        <td>0.4.0.2</td>
    </tr>
    <tr>
        <th>Homepage</th>
        <td><a href="http://arachni-scanner.com">http://arachni-scanner.com</a></td>
    </tr>
    <tr>
        <th>Blog</th>
        <td><a href="http://trainofthought.segfault.gr/category/projects/arachni/">http://trainofthought.segfault.gr/category/projects/arachni/</a></td>
    <tr>
        <th>Github page</th>
        <td><a href="http://github.com/zapotek/arachni">http://github.com/zapotek/arachni</a></td>
     <tr/>
    <tr>
        <th>Documentation</th>
        <td><a href="http://github.com/Zapotek/arachni/wiki">http://github.com/Zapotek/arachni/wiki</a></td>
    </tr>
    <tr>
        <th>Code Documentation</th>
        <td><a href="http://zapotek.github.com/arachni/">http://zapotek.github.com/arachni/</a></td>
    </tr>
    <tr>
        <th>Google Group</th>
        <td><a href="http://groups.google.com/group/arachni">http://groups.google.com/group/arachni</a></td>
    </tr>
    <tr>
       <th>Author</th>
       <td><a href="mailto:tasos.laskos@gmail.com">Tasos Laskos</a></td>
    </tr>
    <tr>
        <th>Twitter</th>
        <td><a href="http://twitter.com/Zap0tek">@Zap0tek</a></td>
    </tr>
    <tr>
        <th>Copyright</th>
        <td>2010-2012 Tasos Laskos</td>
    </tr>
    <tr>
        <th>License</th>
        <td><a href="file.LICENSE.html">GNU General Public License v2</a></td>
    </tr>
</table>

![Arachni logo](http://zapotek.github.com/arachni/logo.png)

## Synopsis

Arachni is a feature-full, modular, high-performance Ruby framework aimed towards helping
penetration testers and administrators evaluate the security of web applications.

Arachni is smart, it trains itself by learning from the HTTP responses it receives during the audit process and
is able to perform meta-analysis using a number of factors in order to correctly assess the trustworthiness of results and intelligently identify false-positives.

Unlike other scanners, it takes into account the dynamic nature of web applications, can detect changes caused while travelling<br/>
through the paths of a web application's cyclomatic complexity and is able to adjust itself accordingly.<br/>
This way attack/input vectors that would otherwise be undetectable by non-humans are seamlessly handled by Arachni.

Moreover, Arachni yields great performance due to its asynchronous HTTP model (courtesy of [Typhoeus](https://github.com/pauldix/typhoeus)) --
especially when combined with a High Performance Grid setup which allows you to combine the resources of multiple nodes for lightning fast scans.<br/>
Thus, you'll only be limited by the responsiveness of the server under audit.

Finally, it is versatile enough to cover a great deal of use cases,
ranging from a simple command line scanner utility, to a global high performance grid of scanners, to a Ruby library allowing for scripted audits.

**Note**: _Despite the fact that Arachni is mostly targeted towards web application security, it can easily be used for general purpose scraping, data-mining, etc with the addition of custom modules._


### Arachni offers:

#### A stable, efficient, high-performance framework

Module, report and plugin writers are allowed to easily and quickly create and deploy their components
with the minimum amount of restrictions imposed upon them, while provided with the necessary infrastructure to accomplish their goals.<br/>
Furthermore, they are encouraged to take full advantage of the Ruby language under a unified framework that will increase their productivity
without stifling them or complicating their tasks.<br/>

#### Simplicity
Although some parts of the Framework are fairly complex you will never have to deal them directly.<br/>
From a user's or a component developer's point of view everything appears simple and straight-forward all the while providing power, performance and flexibility.

## Feature List

### General

 - Cookie-jar support.
 - Custom header support.
 - SSL support.
 - User Agent spoofing.
 - Proxy support for SOCKS4, SOCKS4A, SOCKS5, HTTP/1.1 and HTTP/1.0.
 - Proxy authentication.
 - Site authentication (Automated form-based, Cookie-Jar, Basic-Digest, NTLM and others)
 - Highlighted command line output.
 - UI abstraction:
    - Command line UI
    - Web UI (Utilizing the Client - Dispatcher RPC infrastructure)
 - Pause/resume functionality.
 - High performance asynchronous HTTP requests.
 - Open [RPC](https://github.com/Zapotek/arachni/wiki/RPC-API) Client/Dispatcher Infrastructure
    - [Distributed deployment](https://github.com/Zapotek/arachni/wiki/Distributed-components)
    - Multiple clients
    - Parallel scans
    - SSL encryption (with peer authentication)
    - Remote monitoring
    - Support for [High Performance Grid](https://github.com/Zapotek/arachni/wiki/HPG) configuration, combining the resources of multiple nodes to perform fast scans.

### Website Crawler

 - Filters for redundant pages like galleries, catalogs, etc based on regular expressions and counters.
 - URL exclusion filter based on regular expressions.
 - URL inclusion filter based on regular expressions.
 - Can optionally follow subdomains.
 - Adjustable link count limit.
 - Adjustable redirect limit.
 - Modular path extraction via "Path Extractor" components.
 - Can read paths from multiple user supplied files (to both restrict and extend the scope of the crawl).

### HTML Parser

Can extract and analyze:

 - Forms
 - Links
 - Cookies
 - Headers

The analyzer can graciously handle badly written HTML code due to a combination of regular expression analysis and the [Nokogiri](http://nokogiri.org/) HTML parser.

###  Module Management

 - Very simple and easy to use module API providing access to multiple levels of complexity.
 - Helper audit methods:
    - For forms, links and cookies auditing.
    - A wide range of injection strings/input combinations.
    - Writing RFI, SQL injection, XSS etc modules is a matter of minutes if not seconds.
 - Currently available modules:
    - Audit:
        - SQL injection
        - Blind SQL injection using rDiff analysis
        - Blind SQL injection using timing attacks
        - CSRF detection
        - Code injection (PHP, Ruby, Python, JSP, ASP.NET)
        - Blind code injection using timing attacks (PHP, Ruby, Python, JSP, ASP.NET)
        - LDAP injection
        - Path traversal
        - Response splitting
        - OS command injection (*nix, Windows)
        - Blind OS command injection using timing attacks (*nix, Windows)
        - Remote file inclusion
        - Unvalidated redirects
        - XPath injection
        - Path XSS
        - URI XSS
        - XSS
        - XSS in event attributes of HTML elements
        - XSS in HTML tags
        - XSS in HTML 'script' tags
    - Recon:
        - Allowed HTTP methods
        - Back-up files
        - Common directories
        - Common files
        - HTTP PUT
        - Insufficient Transport Layer Protection for password forms
        - WebDAV detection
        - HTTP TRACE detection
        - Credit Card number disclosure
        - CVS/SVN user disclosure
        - Private IP address disclosure
        - Common backdoors
        - .htaccess LIMIT misconfiguration
        - Interesting responses
        - HTML object grepper
        - E-mail address disclosure
        - US Social Security Number disclosure
        - Forceful directory listing
        - Mixed Resource/Scripting
    - Extras
        - SVN Digger dirs
        - SVN Digger files
        - RAFT dirs
        - RAFT files


### Report Management

 - Modular design.
 - Currently available reports:
    - Standard output
    - HTML (Cheers to [Christos Chiotis](mailto:chris@survivetheinternet.com) for designing the new HTML report template.)
    - XML
    - TXT
    - AFR -- The default Arachni Framework Report format.
    - JSON
    - Marshal
    - YAML
    - Metareport -- Providing Metasploit integration to allow for [automated and assisted exploitation](http://zapotek.github.com/arachni/file.EXPLOITATION.html).

### Plug-in Management

 - Modular design
 - Plug-ins are framework demi-gods, they have direct access to the framework instance.
 - Can be used to add any functionality to Arachni.
 - Currently available plugins:
    - ReScan -- It uses the AFR report of a previous scan to extract the sitemap in order to avoid a redundant crawl.
    - Passive Proxy -- Analyzes requests and responses between the web app and the browser assisting in AJAX audits, logging-in and/or restricting the scope of the audit
    - Form based AutoLogin
    - Dictionary attacker for HTTP Auth
    - Dictionary attacker for form based authentication
    - Profiler -- Performs taint analysis (with benign inputs) and response time analysis
    - Cookie collector -- Keeps track of cookies while establishing a timeline of changes
    - Healthmap -- Generates sitemap showing the health of each crawled/audited URL
    - Content-types -- Logs content-types of server responses aiding in the identification of interesting (possibly leaked) files
    - WAF (Web Application Firewall) Detector -- Establishes a baseline of normal behavior and uses rDiff analysis to determine if malicious inputs cause any behavioral changes
    - AutoThrottle -- Dynamically adjusts HTTP throughput during the scan for maximum bandwidth utilization
    - TimingAttacks -- Provides a notice for issues uncovered by timing attacks when the affected audited pages returned unusually high response times to begin with.</br>
         It also points out the danger of DoS attacks against pages that perform heavy-duty processing.
    - Uniformity -- Reports inputs that are uniformly vulnerable across a number of pages hinting to the lack of a central point of input sanitization.
    - Discovery -- Performs anomaly detection on issues logged by discovery modules and warns of the possibility of false positives where applicable.
    - BeepNotify -- Beeps when the scan finishes.
    - LibNotify -- Uses the libnotify library to send notifications for each discovered issue and a summary at the end of the scan.
    - EmailNotify -- Sends a notification (and optionally a report) over SMTP at the end of the scan.
    - Manual verification -- Flags issues that require manual verification as untrusted in order to reduce the signal-to-noise ratio.
    - Resolver -- Resolves vulnerable hostnames to IP addresses.


### Trainer subsystem

The Trainer is what enables Arachni to learn from the scan it performs and incorporate that knowledge, on the fly, for the duration of the audit.

Modules have the ability to individually force the Framework to learn from the HTTP responses they are going to induce.<br/>
However, this is usually not required since Arachni is aware of which requests are more likely to uncover new elements or attack vectors and will adapt itself accordingly.

Still, this can be an invaluable asset to Fuzzer modules.

## [Installation](https://github.com/Zapotek/arachni/wiki/Installation)

### CDE packages for Linux

Arachni is released as [CDE packages](http://stanford.edu/~pgbovine/cde.html) for your convinience.<br/>
CDE packages are self contained and thus alleviate the need for Ruby and other dependencies to be installed or root access.<br/>
You can download the latest CDE package from the [download](https://github.com/Zapotek/arachni/downloads) page and escape the dependency hell.<br/>
If you decide to go the CDE route you can skip the rest, you're done.

### Cygwin packages for Windows

Arachni does not yet run natively on Windows systems, however until that day comes you can download a pre-configured Cygwin environment containing Arachni and its dependencies.
All you need to do is download the [latest self-extracting archive](http://downloads.segfault.gr/arachni/), select a directory for it, open it up and then execute the Cygwin batch file.
You will then be presented with a Bash shell, after that you'll be able to use Arachni as if you were on a Linux system.

### Gem

To install the Gem or work with the source code you'll also need the following system libraries:

    sudo apt-get install libxml2-dev libxslt1-dev libcurl4-openssl-dev libsqlite3-dev

You will also need to have Ruby 1.9.2 (or later) installed *including* the dev package/headers.<br/>
The prefered ways to accomplish this is by either using [RVM](http://rvm.beginrescueend.com/) or by downloading and compiling the source code for [Ruby](http://www.ruby-lang.org/en/downloads/) manually.


To install Arachni:

    gem install arachni

### Source

If you want to clone the repository and work with the source code then you'll need to run the following to install all gem dependencies and Arachni:

    git clone git://github.com/Zapotek/arachni.git
    cd arachni
    rake install


## Usage

### [Command line interface](https://github.com/Zapotek/arachni/wiki/Command-line-user-interface)

### [WebUI](https://github.com/Zapotek/arachni/wiki/Web-user-interface)

### [Starting a Dispatcher](https://github.com/Zapotek/arachni/wiki/RPC-server)


## Configuration of <em>extras</em>

The <em>extras</em> directory holds components that are considered too specialised, dangerous or in some way unsuitable for utilising without explicit user interaction. <br/>
This directory was mainly added to distribute modules which can be helpful but should not be put in the default <em>modules</em> directory to prevent them from being
automatically loaded.

Should you want to use these extra components simply move them from the <em>extras</em> folder to their appropriate system directories.

## Supported platforms

Arachni should work on all *nix and POSIX compliant platforms with Ruby and the aforementioned requirements.

Windows users can download the pre-configured Cygwin package, see the [installation instructions](https://github.com/Zapotek/arachni/wiki/Installation).

## Bug reports/Feature requests
Please send your feedback using Github's issue system at
[http://github.com/zapotek/arachni/issues](http://github.com/zapotek/arachni/issues).


## License
Arachni is licensed under the GNU General Public License v2.<br/>
See the [LICENSE](file.LICENSE.html) file for more information.


## Disclaimer
Arachni is free software and you are allowed to use it as you see fit.<br/>
However, I can't be held responsible for your actions or for any damage
caused by the use of this software.

![Arachni banner](http://zapotek.github.com/arachni/banner.png)
