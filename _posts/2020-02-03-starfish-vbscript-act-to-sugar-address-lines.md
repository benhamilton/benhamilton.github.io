---
layout: post
title: Starfish VBScript Act! to Sugar Address Lines
permalink: 2020-02-03-starfish-vbscript-act-to-sugar-address-lines
published: false
---
The following VBScript can be used as a function in StarfishETL to concatenate (with line breaks) the Address Line 1/2/3 fields into one field.<!--more-->

<pre><code>Function ScriptedField
  dim addr
  addr = "@@ORG:BusinessAddrLine1@@"
  if "@@ORG:BusinessAddrLine2@@"<>"" then addr = addr & vbCrLf & "@@ORG:BusinessAddrLine2@@"<>""
  if "@@ORG:BusinessAddrLine3@@"<>"" then addr = addr & vbCrLf & "@@ORG:BusinessAddrLine3@@"<>""
  ScriptedField=addr
End Function</code></pre>

Another helpful function is one that reformats the datetime field so it's non-ambiguous.

<pre><code>
Function ScriptedField
  ScriptedField=FormatDate("@@ORG:date_entered@@", "yyyy-MM-ddTHH:mm:ss")
End Function
</code></pre>


To pull the email address from Act! including a custom field that shows if the contact has unsubscribed, use the following (changing the custom field name of course):
<pre><code>[{"email_address":"@@ORG:EmailAddress@@","primary_address":true,"opt_out":@@ORG:CUST_Unsubscribed_093926075@@}]</code></pre>
