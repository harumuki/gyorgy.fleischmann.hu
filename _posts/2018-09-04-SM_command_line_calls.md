---
layout:   post
title:    "Service Manager: Command line calls"
author:   flex
comments: true
category: Knowledge / tudás
tags:     [HPE, MicroFocus, SM, Service Manager]
---

# HP / HPE / MicroFocus <br> Service Manager: Command line calls

Az eredeti forrás: [List: Command line calls](https://docs.microfocus.com/SM/9.41/Classic/Content/programming/system_language/reference/list_command_line_calls.htm)

## Generic command line calls:

| Command | RAD application called | Function | Example |
|:------- |:----------------------:|:-------- |:------- |
| *a<application name> | as specified | Runs the specified RAD routine. | *adatabase accesses Database Manager. |
| *f<file name> | database | Accesses a specified file. | *fcontacts accesses the contacts file. |
| *q<query name> | query.stored | Runs a stored query. | *qIM.open.ALL displays a list of all open incidents. |
| *s<script name> | script.execute | Runs the specified script. | *socmq.open.hr.quote opens an HR Request record. |
| #<shortcut name> | non-applicable | Queries for a list of shortcut commands. | #do presents a list of commands that start with “do.” |

## Direct command line calls:

| Command | RAD application called | Function |
|:------- |:----------------------:|:-------- |
| **about** | bulletin.key | Displays the system bulletin and any active “hot” incidents.
| **ag** | encl.appl | Displays the RAD Editor prompt (formerly known as Application Generator). |
| **agcompare** | compare.applications | Displays the RAD Application Comparison form. |
| **agentrev** | query.stored | Executes the “agentrev” query which displays a list of the schedule records for all SCAuto agents. |
| **agentstat** | scauto.check.setup | Displays a currently-available SCAuto agents. Form includes options for stopping agents |
| **agmap** | agmap.sched | Displays the Application Mapping form. |
| **agr** | report.exerciser | Executes the “OPEN PROBLEM ANALYSIS REPORTS - ASSIGNMENT GROUP” report via Report Exerciser. |
| **alert** | database | Displays the Alert Definition form. |
| **alertdefs** | se.search.engine | Displays the Alert Definition form. |
| **alertlogs** | se.search.engine | Displays the Alert Log form. |
| **appr** | database | Displays the Approval Definition form. |
| **approvaldefs** | se.search.engine | Displays the Approval Definition form. |
| **approvallogs** | se.search.engine | Displays the Approval Log form. |
| **asr** | report.exerciser | Executes the “ALERT STATUS REPORT” report via Report Exerciser. |
| **auditdelta** | audit.unload.front | Displays the form for unloading an Audit Delta. |
| **audithist** | database | Displays the Audit History form. |
| **auditonoff** | database | Displays the Audit Control form. |
| **audlog** | database | Displays the Audit Log form. |
| **audspec** | database | Displays the Audit Specification Table form. |
| **autoshut** | database | Displays the Automatic Shutdown Information form. |
| **bulletin** | database | Displays the System Bulletin form. |
| **calduty** | database | Displays the Normal Working Hours form. |
| **calholiday** | database | Displays the Holiday Names form. |
| **call** | exercise | Displays the Application Exerciser form for testing/running a RAD application directly. |
| **callqueue** | sc.setup.manage | Displays the Interaction) queue. |
| **chgqueue** | sc.setup.manage | Displays the Change queue. |
| **cls** | pm.access | Displays the Incident queue. |
| **cm3grp** | database | Displays the Change Management Groups Definition form. |
| **cm3msg** | database | Displays Change Management Event Definition form. |
| **cm3profile** | database | Displays the Change Management (ChM) Security Profile form. |
| **cm3r** | se.search.engine | Displays the search form for Change Management requests. |
| **cm3rcat** | cm3r.category.maint | Displays the Change Management Request Category form. |
| **cm3renv** | se.search.engine | Displays the Change Management Application Environment form. |
| **cm3ropen** | cmc.open.from.menu | Initiates the script for opening a new change request record. |
| **cm3t** | se.search.engine | Displays the search form for Change Management tasks. |
| **cm3tcat** | cm3t.category.maint | Displays the Change Management Task Category form. |
| **cm3tenv** | se.search.engine | Displays the Change Management Application Environment - Tasks form. |
| **cm3topen** | cmt.open.from.menu | Initiates the script for opening a new change task. |
| **cmcontrol** | cm.edit.config | Displays the Contract Management Configuration form. |
| **cmdlist** | report.exerciser | Executes the Menu Command List report via Report Exerciser. |
| **comp** | se.search.engine | Displays the System Information Definition form (system Company record). |
| **compare** | compare.applications | Displays the RAD Application Comparison form. |
| **configure sla** | sla.edit.config | Displays the Service Level Agreement Control form. |
| **contacts** | database | Displays the Contacts search form. |
| **copyfile** | copy.database.file | Initiates the script for copying a database file. |
| **createschd** | database | Displays the Schedule form. |
| **curalerts** | se.search.engine | Displays the Alert search form. |
| **curapprovals** | se.search.engine | Displays the Approval search form. |
| **curconvert** | database | Displays the Currency Conversion search form. |
| **currency** | database | Displays the Currency form. |
| **datamap** | database | Displays the Data Map form. |
| **db** | database | Displays the Database Manager form. |
| **dbdict** | dbdict.utility database | Displays the Database Dictionary prompt. |
| **de** | database | Displays the Display Application Event Definition form. |
| **delmail** | database | Displays the form for sending internal Service Manager broadcast mail. |
| **dist** | database | Displays the Distribution Group form. |
| **do** | database | Displays the Display Application Option Definition form. |
| **doc** | menu.manager | Displays the menu with options for maintaining the document engine. **Note:** This command line call will only work if **the menu forms are being displayed.|
| **ds** | database | Displays the Display Application Screen Definition form. |
| **edit gkn** | database | Displays the form for editing core knowledge. |
| **err** | report.exerciser | Executes the “EXCESSIVE REASSIGNMENT REPORT” report via Report Exerciser. |
| **evemail** | sca.window | Displays the form for sending an email event. |
| **eventbld** | axces.build.maps | Initiates the wizard for building event mappings. |
| **eventfltr** | database | Displays the Event Filters form. |
| **eventin** | database | Displays the Event Services input queue. |
| **eventmap** | database | Displays the Event Map form. |
| **eventout** | database | Displays the Event Services output queue. |
| **eventreg** | database | Displays the Event Registration form. |
| **evicmbld** | scauto.build.maps | Initiates a script for building Configuration Management event mappings. |
| **evwrite** | sca.window | Displays the form for sending an Incident Management, Configuration Management, or generic event. |
| **expline** | database | Displays the Expense Line Information form. |
| **fc** | format.ctrl.maint | Displays the Format Control form. |
| **fd** | forms.designer | Displays the Forms Designer form. |
| **files** | database | Displays the Configuration File form for database unloads. |
| **formatctrl** | format.ctrl.maint | Displays the Format Control form. |
| **forms** | forms.designer | Displays the Forms Designer prompt. |
| **gen core** | ke.gencore.verify | Displays the prompt for generating the core Knowledge Base. |
| **gl** | database | Displays the global list form. |
| **hd** | pm.access | Displays the Incident queue. |
| **htopic** | database | Displays the Help topic search form. |
| **imapplenv** | database | Displays the Incident Management Environment Profile form. |
| **imassign** | database | Displays the Assignment Groups form.
| **imbuild** | pm.build.probsum | Initiates the script for the building of probsummary records.
| **imconvert** | pm.convert.format | Displays the Convert Incident Format form. |
| **imgroups** | database | Displays the Incident Management Groups form. |
| **improfile** | database | Displays the Incident Management Security Profile form. |
| **imreset** | pm.clear.downtime | Allows for the clearing of availability information. |
| **inact** | kill.inactive.setup | Displays the Kill Inactive Users Setup Parameters form. |
| **incidentqueue** | sc.setup.manage | Displays the Incident queue. |
| **info** | database | Displays the Background Processor Initialization Registry form. |
| **irassg** | report.exerciser | Executes the Problem Response Analysis By Assignment report via Report Exerciser. |
| **ircomp** | report.exerciser | Executes the Problem Response Analysis By Component report via Report Exerciser. |
| **irloc** | report.exerciser | Executes the Problem Response Analysis By Location report via Report Exerciser. |
| **irq** | ir.query.window | Displays the form for issuing an IR Query File form. |
| **irvend** | report.exerciser | Executes the “Problem Response Analysis By Vendor” report via Report Exerciser. |
| **knowledge** | get.search.application | Displays the search form for Knowledgebase information. |
| **link** | edit.link | Displays the Link File form. |
| **linklist** | report.exerciser | Executes the Link File Listing report via Report Exerciser. |
| **load transfer** | apm.upgrade.load.transfer | Initiates the Service Manager Upgrade Utility Load Transfer form. |
| **location** | database | Displays the Location form. |
| **logmsg** | database | Displays the “log” type Message Class form. |
| **mailmsg** | database | Displays the “mail” type Message Class form. |
| **mcf** | database | Displays the Capability Word form. |
| **menu** | database | Displays the Menu form. |
| **message** | database | Displays the Message form. |
| **model** | database | Displays the Configuration Item (CI) Model search form. |
| **modelicm** | database | Displays the Configuration Item (CI) Model search form. |
| **modelven** | database | Displays the Model Vendor Information form. |
| **monitor** | system.monitor | Displays the system status form. |
| **msg** | database | Displays the generic Message Class form. |
| **msglog** | database | Displays the Message Log form. |
| **msgtype** | database | Displays the Message Type form. |
| **new call** | cc.first | Displays a blank form to create a Service Desk interaction. |
| **new incident** | apm.first | Displays a blank incident form for record entry. |
| **note** | database | Displays the Notification Definition form. |
| **number** | database | Displays the Sequential Number form. |
| **ocmbldlvl** | ocm.co.bld.lvls | Displays the prompt for updating all of the level numbers for all components in the model file. |
| **ocmco** | database | Displays the Configuration Item (CI) Model search form. |
| **ocmdeliv** | report.exerciser | Executes the Delivery Forecast for Next 7 Days report via Report Exerciser. |
| **ocmdreqj** | report.exerciser | Executes the Daily Quote Log report via Report Exerciser. |
| **ocmdrj** | report.exerciser | Executes the Daily Receipt Journal report via Report Exerciser. |
| **ocmevents** | database | Displays the Request Management Events form. |
| **ocmgroups** | database | Displays the Request Management Group Definition form. |
| **ocml** | ocml.access | Displays the search form for Request Management line items |
| **ocmlcat** | database | Displays the Request Management Line Item Category form. |
| **ocmlcreate** | ocm.category.create | Displays the Request Management Line Item Category form. |
| **ocmlenvir** | query.stored | Displays the Request Management Line Items Application Environment form. |
| **ocmlmast** | database | Displays the Request Management Catalog Select Categories form. |
| **ocmlphase** | database | Displays the Request Management Line Item Phase form. |
| **ocmlrec** | database | Displays the Request Management Receiving Log form. |
| **ocmo** | ocmo.access | Displays the search form for Request Management orders. |
| **ocmoappr** | ocmo.access | Displays a list of orders that have been approved. |
| **ocmocat** | database | Displays the Request Management Order Category form. |
| **ocmocavail** | database | Displays the Request Management Check Availability Order Generation Schedule Record. |
| **ocmocreate** | ocm.category.create | Displays the Request Management Order Category form. |
| **ocmodemand** | database | Displays the Request Management Background Order Generation Schedule Record form. |
| **ocmoenvir** | query.stored | Displays the Request Management Orders Application Environment form. |
| **ocmoopen** | ocmo.access | Initiates the script for creating a new Request Management order. |
| **ocmophase** | database | Displays the Request Management Order Phase form. |
| **ocmpo** | report.exerciser | Executes the Print Purchase Orders report via Report Exerciser. |
| **ocmprofile** | database | Displays the Request Management Profile form. |
| **ocmq** | ocmq.access | Displays the search form for Request Management quotes. |
| **ocmqcat** | database | Displays the Request Management Quote Category form. |
| **ocmqcreate** | ocm.category.create | Displays the Request Management Quote Category form. |
| **ocmqopen** | ocmq.access | Initiates the script for creating a new Request Management quote. |
| **ocmqphase** | database | Displays the Request Management Quote Phase form. |
| **ocmvenper** | report.exerciser | Executes the Vendor Performance Based on Line Item Dates report via Report Exerciser. |
| **odr** | report.exerciser | Executes the OPEN PROBLEM ANALYSIS REPORTS - DOCUMENT NUMBER report via Report Exerciser. |
| **oncall** | database | Displays the On Call Schedule contact form. |
| **oncallsched** | database | Displays the On Call Schedule calendar form. |
| **operator** | database | Displays the Operator form. |
| **opn** | pm.access | Displays the Incident queue. |
| **overspent** | query.stored | Executes the "overspent contracts" query which displays a list of all service contracts that have exceeded their **financial budget. |
| **password** | password.change | Displays the prompt for changing the login password. |
| **print** | report.exerciser | Executes the Print of Application report via Report Exerciser. |
| **printappl** | report.exerciser | Executes the Print of Application report via Report Exerciser. |
| **prtmsg** | database | Displays the "print" type Message Class form. |
| **purgarch** | pa.main.appl | Displays the Purge/Archive form. |
| **purgeaudit** | audit.purge | Displays the form for purging audit history. |
| **RAD** | encl.appl | Displays the RAD Editor prompt. |
| **rad** | encl.appl | Displays the RAD Editor prompt. |
| **re** | report.exerciser | Displays the Report Exerciser prompt. |
| **recalc partials** | sla.recalc.totals | Displays the prompt for recalculating SLA information over a given time frame. |
| **report** | report.exerciser | Displays the Report Exerciser prompt. |
| **review cc** | cc.setup.manage | Displays the Service Desk Interaction queue. |
| **review im** | apm.setup.manage | Displays the Incident queue. |
| **rmail** | read mail | Displays the prompt for selecting which type of internal Service Manager mail to read. |
| **run** | exercise | Displays the Application Exerciser form for testing/running a RAD application directly. |
| **rv** | pm.access | Displays the Incident queue. |
| **rw** | report.writer | Displays the Report Writer prompt. |
| **sch** | database | Displays the Schedule File form. |
| **schedule** | database | Displays the Schedule File form. |
| **schmail** | mail.set.schedule | Displays the form for scheduling background mail. |
| **scknowledge** | get.search.application | Displays the Knowledgebase search form. |
| **scmsg** | database | Displays the Service Manager Message form. |
| **scr** | report.exerciser | Executes the "shift change report" report via Report Exerciser. |
| **scripts** | script.maint | Displays the Script Definition form. |
| **search cal** | cc.search.incidents | Displays the search form for Service Desk interactions. |
| **search calls** | cc.search.incidents | Displays the search form for Service Desk interactions. |
| **search incident** | apm.search.problems | Displays the search form for Incident Management incidents. |
| **search sla** | sla.search.objects | Displays the search form for Service Level Agreements. |
| **servcont** | database | Displays the Service Contract form. |
| **shutdown** | system.shutdown | Initiates the process for shutting down the Service Manager server. |
| **smail** | mail.send.appl | Displays the prompt for confirming the sending of internal Service Manager mail. |
| **smapplenv** | database | Displays the Service Desk Environment form. |
| **smgroups** | database | Displays the Service Desk Groups form. |
| **smprofile** | database | Displays the Service Desk Security Profile form. |
| **software** | database | Displays the Software Management form. |
| **sol cans** | se.search.engine | Displays the Pending Knowledge Items form. |
| **spool** | spool.scheduler | Displays the Spoolheader form. |
| **sq** | database | Displays the Stored Query Maintenance form. |
| **start** | apm.upgrade.main | Initiates the Upgrade Utility wizard. |
| **status** | system.status | Displays the system status form. |
| **stdptrs** | database | Displays the Configuration File form for standard printers. |
| **subtotals** | database | Displays the Subtotal Definition form. |
| **syslog** | database | Displays the System Log form. |
| **task** | query.stored | Displays a list of the user’s change tasks. |
| **terminals** | database | Displays the Terminal Configuration form. |
| **triggers** | database | Displays the triggers form. |
| **tskqueue** | sc.setup.manage | Displays the Task queue. |
| **unload** | us.unload | Displays a list of unload scripts. |
| **uoperprof** | query.stored | Displays the Operator Status Display form. |
| **upd** | pm.access | Displays the Incident queue. |
| **userlevel** | us.userlevel | Displays the current user access level and the options for changing this access. |
| **userstats** | report.userstats | Displays the prompt for executing the Usage Statistics report. |
| **usrcmr** | cm3r.main | Initiates the script for opening a new change request record. |
| **usrdir** | database | Displays the Contacts form. |
| **usricm** | icm.access | Displays the Configuration Item Search form. |
| **usrknow** | database | Displays the search form for Knowledge Base information. |
| **usrocma** | ocmo.access | Displays a list of the current Request Management orders. |
| **usrocmo** | ocmo.access | Displays the search form for Request Management orders. |
| **validity** | se.search.engine | Displays the Validity Table Specifications form. |
| **vendor** | database | Displays the Vendor/Manufacturer search form. |