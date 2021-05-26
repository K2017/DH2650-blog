##
##-----------------------------------
## Remove dialog box from menu
##-----------------------------------
##
#set($foreach = "")
#set($word = "")
#set($nofileext[0] = "")
#set($rmspace[0] = "")
#set($rmspace[1] = "")
#set($rmspace[2] = "")
##
##-----------------------------------
## Actual Code Starts Here
##-----------------------------------
##
#set ($rmspace = $NAME.split("-"))
#set ($title="")
#foreach($word in $rmspace)
#if($foreach.count > 3)
#set ($title = "$title $word")
#end
#end
##
##-----------------------------------
##YAML
##-----------------------------------
##
---
layout: post
title: $title
status: $status
type: post
date: $rmspace[0]-$rmspace[1]-$rmspace[2] ${HOUR}:${MINUTE}
published: true
comments: true

---