# org.eclipse.jface.text
Modified plugin for auto completion in eclipse 修改eclipse自动补全插件

# Version
org.eclipse.jface.text_3.9.2.v20141003-1326

# Description
If you can read Chinese please visit here.中文博客
http://www.cnblogs.com/pelloz/p/4343208.html
This plugin is taken from eclipse 4.4.2 and is modified a little to improve auto completion user experiences.

Generally, it enables Tab key to down select word candidates. Also it disables some annoying auto completion behaviors like ";"\"="\"space".
The position I modified is "org.eclipse.jface.text/src/org.eclipse.jface.text.contentassist/CompletionProposalPopup.java",from line 1361 to line 1371.
Modify
fProposalShell.setFocus();
returnfalse;
To
insertSelectedProposalWithMask(e.stateMask);
break;
Modify
if(contains(triggers, key))
To
if(key!=0x20&& key!='='&& key!=';'&& contains(triggers, key))

It is recommended that the user set 'Window->Preferences, Java->Editor->Content Assist, Content Assist->Auto Activation->Auto Activation triggers for java' to ' .abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ_'

#How to use
Use Eclipse to Import the whole source to workspase,check the code like above,then Export－>Deployable plugins and fragments,click Next,choose Destination TabControl,choose Directory and Finish.A new file was generated like "org.eclipse.jface.text_3.9.2.v20141003-1326.jar",copy the jar file to Eclipse's installation directory "./eclipse/plugins/" and cover the original one.Of coures you'd better to backup the original one for insurance purposes.At last,reboot the Eclipse.
