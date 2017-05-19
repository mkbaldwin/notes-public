# CodeStock 2016

 * July 15 - 16, 2016
 * Knoxville Convention Center

## Day 1 (6/15/2016)

### Keynote

Cory House (@housecor)

> Why be in the mainstream? You can Google it.

> Everybody gets a COBOL book!

### Session 1: Security Vulnerabilities

Joe Kunk

 * Risk = Event Probability x Business Impact
 * Attacks tend to fall into a small number of categories
 * fireeye.com
 * Bring your own device (BYOD)
   * More Challenges for Security
 * Devices that can impersonate an open access point. Then capture all data then
   relay to the real device. Thus allowing someone to capture all traffic including
   SSL keys.
    * Mitigate with VPN client
 * Ransomware - Encrypt data and then hold the keys for ransom
   * getting much smarter
   * very dangerous
   * These are a business. Demand payment in BitCoin. Even have "customer support"
     to help people pay.
   * 3X more ransomware apps for mobile devices in the past year.
   * Recent offline backup (physical disconnect) are only real protection
 * Most attacks are random and not targeted at anyone specific
   * Throw it out and see who they catch
 * Attack types
   * SQL Injection
     * Most common
     * Easy fix
   * Cross site scripting (XSS)
   * Cross site request forgery (CSRF)

### Session 2: Responsive Frameworks Fine Print

Aaron Ladage (@aladage)

 * It took 3 years from the iPhone release to the advent of responsive
   * new learning curve
   * can't test all sizes
   * how to design for it?
   * performance is important for mobile
 * JQuery Mobile
 * Zurb (Zerb?)
 * Sencha
 * Ionic
 * Bootstrap - 2011
   * Built by twitter for use on internal Tools
 * Frameworks do ... well:
   * make getting started easier
   * rapid prototyping
   * consistent design language / coding style
   * provides a grid for you
 * The Bad:
   * Websites can look alike
     * customize defaults
   * The right tool for the job
     * Lots of stuff included might not be needed
     * Strip out what you don't need
   * Performance is key
     * 250ms slower/faster is the competitive advantage - Microsoft
     * Minify
     * Combine into one file
     * Don't override default styles, recompile from less
   * What happens if you redesign?
     * Bootstrap markup is all tied to visual layout
   * What if the framework changes?
     * Bootstrap has already done this with V3 and with some V4 stuff.
   * Leverage the preprocessor to create symantic markup that extends the Bootstrap classes
     * eg
     ```
       .article {
         @extend :col-xs-12
       }
     ```
   * Makes upgrading / moving away Easier
   * Be Framework Agnostic

### Session 3: Skipped for IOT Workshop

Losant IOT Platform
