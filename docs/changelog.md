
# Changelog

## 0.4.0 <small>- December 2, 2020</small>
* New App: Send Message to Calling Number - for Post Call Surveys
* New App: Webhooks (migrated from existing Webhook feature)
* New MCID Page - CDR Status, and MCIDs
* New Bulk Rule Import/Export - Import/Export multiple rules in bulk
* New IOS Rule Import / Export - direct from IOS translation rules
* New CDR Parser: Rebuilt CDR parser for stability.
* New Organization Feature: - Add multiple team members to an Organization to manage policies.
* CDR MCID: Prior to 0.4.0 - CDR MCID were added to the "Default Policy" only. Now they are stored in a Organization MCIDs Table.
* Added ability for policies to block on MCIDs, or ignore them.
* Daily SQL backups on the OVA
* Breaking Changes:
  * WebHooks are now an App.
* Because of many database changes for Organization Ownership - This upgrade will cause a loss of data. Backup manually before updating.
* Kubernetes manifest is not ready for 0.4.0 yet - coming soon.
  
## 0.3.9 <small>- 11/5/2020</small>
* New: Apps - Customizable App structure.
* New: App: Native Webex Teams Alert 
* New: App: Native SMTP Alert 
* New: App: Native SMS Alert 
* New: Added Manual CDR Upload to CDR Reports page
* New: Added Parser support for CUCM 12.5 CDR.
* Change: Beta Build Expires 1/31/2021
* Breaking Changes:
  * "Alerts" are now within Apps. This allows full customization of the Alert in any format - Teams, SMS, SMTP, or whatever comes next.
  * Removed Alerts Tab in Rule Edit.
  * Removed SMTP Settings Page - SMTP Settings are now part of Apps.
  * Previously defined SMTP/Email Alerts will still work this release as transition release - but will not show up in the UI. This feature will be officially removed in 0.4.0.
  
## 0.3.8 <small>- 9/24/2020</small>
* New: *Webhooks / Apps * - Add multiple HTTP triggers to any realtime call event! Apps are coming and will be even smarter.
* New: OVA Pre-Built Appliance Release
* *UI Updates* - Many UI enhancements, more to come.
* New: Documentation Site - [here](https://calltelemetry.readthedocs.io/)
* New: *Expire MCID submissions* - Configure a day limit for user submissions to automatically expire/delete.
* New: Policies UI consolidated - history, search, live logs, all from the Policies View.
* New: Improved Settings Page with Tabs
* Fixed: *SMTP* - had some issues found in testing.
* Fixed: Hit counters.
* This version is still unlimited and this release expires on 12/31/2020
* Fixed: Standardized time entries to UTC.
* Removed Discord Community Link.
* Added Webex Teams - you can now join a dedicated room in Cisco Webex Teams - see footer.
  
## 0.3.7 <small>- 8/5/2020</small>
* Added *Live Logging* - Streaming logs of realtime call processing for CURRI_API. Now you can see calls and policy decisions made - in Realtime.
* Updated *CDR Uploads* Page - Now you can upload multiple CDR files via drag and drop. CDR will be processed to the Log View, where every field is decoded, and Malicious caller tags are written into your default policy.
* Added *Called Party Translation* - reroute callers to any new number using Policies.
* Added *Calling Party / Calling Name * - change the caller ID of any call in realtime.
* Added *Event Bus* - This is currently more an internal feature, and optimizes realtime responses and lays work for third more exciting integrations.
## 0.3.6 <small>- 7/20/2020</small>
* Updated, tested and Simplified documentation.
* Removed Linux option compiled per Distro. If you need linux only and no docker, let me know.
* Add **Email Alerts** + SMTP Support.
  * You can now receive an Instant Email Alerts on any Route Point, Translation, or Phone Number - including Emergency Alerts like 911 Patterns. CDR not required, and more than one email address can be added.

## 0.3.5 <small>- 3/20/2020</small>
* Add **Greeting Injection** support for Permit and Block Actions.
    * You can now inject greetings without blocking calls - for example to inject a Coronavirus greeting to every call into your cluster.
    * You can use this by typing the exact name of the greeting in Callmanager Announcements into the rule, shown below.
* Add **Permit** action - you can now have policies that do not block.
* Add **default action** - calling and called numbers can be blank to match all calls in a policy.

## 0.3.4 <small>- 3/15/2020</small>
"Call Actions/Triggers" are coming soon, but every feature includes the UI complexity. I focused on this release to be simpler to use, easier to deploy, and better tested.

Web Pages & How-to Videos: 
* Video training on deployment and onboarding

Elixir/Phoenix: 
* Updates to latest versions, including minor refactoring to comply with library changes.

UI:
* Intense effort to simplify, and build easier to understand User Interface.
* Quick Add of numbers for manual entry

![quick](/images/releasenotes/quick-add.gif) {:height="50%" width="50%"}
* Policy Keepalive - shows multiple Health status for each Policy's Keepalive to Callmanager. It also detects failure, and shows the last time seen.

![health](/images/releasenotes/policy-health.png) {:height="30%" width="30%"}

* Call Logs - 
    * View Live CURRI API Calls.
    * Quick Block / Permit Toggle
    * Policy result history tracking

![health](/images/releasenotes/call-logs.gif) {:height="50%" width="50%"}
 
* Moved version to Navbar, simplified Navbar
* CDR UI cleaned up

Deployment:
* Improved Documentation on Docker Install
* Added Kubernetes Deployment Model

Support: 
* Intensely tested every part of the application.
* Removed Slack Channel (invite process is messy)
* Added Discord Channel - easy to join, no invite process.
* Removed Twitter Handle - I'm not using it yet.


## 0.3.3 <small>- 2/27/2020</small>
## Enhancements
* Called party rules. Policies can now be Calling, Called, or Both party matches now. Rules have a calling and called field. Policy type determines what is used. 
* UX Enhancements
* Time limits removed, no expiration date.

## 0.3.2 <small>- 12/10/2019</small>
### New Features
* SIP Service - Point a route pattern at a Callmanager SIP Trunk towards the IP of the CallTelemetry host (on-premise), and you can now transfer calls to add them to the call block list. 
* UX Enhancements

### Bug Fixes
* Call Pagination issues

## 0.3.1 <small>- 12/4/2019</small>

### New Features
Introducing the Industry First CDR to CURRI Integration, allowing automatic incoming call blocking!
* SFTP Server - To accept CDR uploads from Callmanager. Tightly integrated so that the login is exactly the same as the Web Interface of your server.
* CDR Parser - Full support of all CDR(Call Detail Record) fields from Cisco UCM viewable in the web UI. We support 11.x and 12.x. If you have errors send an example of your failed CDR file to me, I can easily add more parsers.
* MCID Automatic Blocking - Detection of Malicious Caller-ID (MCID) flag and automatically blacklisting the caller without any interaction beyond the user pressing the MCID softkey.

#### Upgrading to 0.3.1
Update your docker-composer versions to 0.3.1 to get the new build.

``` bash
git clone https://github.com/calltelemetry/calltelemetry.git
cd calltelemetry

docker-compose up (add -d for daemon in background)
```

## 0.2.9 <small>- 11/1/2019</small>
First Public Release for On-Prem. 

0.2.9 expires Feb 1 2020.
### New Features
* Cisco Incoming Call Blocking - You can apply a call block policy to any Route Pattern, Translation, or Directory Number. You can spread that to multiple CUCM Clusters to have complete call blocking globally.
* Call Logging - All calls from devices using the policy are available in the CURRI Call log.

##  Version 0.2.0 <small>- 9/1/2019</small>
Cloud only. Proof of concept available for public demo.