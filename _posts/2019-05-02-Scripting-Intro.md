
Most of the time those Notepad++ (or insert favorite text editor) templates are enough. Especially once an environment is built and you are performing the same tasks day after day. But let's say you are building out a new environment or migrating from one platform to another in which configs aren't compatible. There are a lot of similar configuration items but the input is just slightly different. Let's use migrating from a Juniper EX series switch to a Nexus switch for example.

What you would normally do is do type **show vlan brief** on the Juniper and then get output something like the following:

Name    |       Tag     |       Address         |       Ports
------- | ------------- | --------------------  | -------------------
Accounting      | 101   |                       |0/1,0/2,0/10,0/15
HR              | 203   |                       |0/3,0/5,0/17
Marketing       | 372   |                       |0/8,0/9,0/11
IT              | 500   |                       |0/13,0/23,0/31

With only four VLANs this is pretty manageable but if this happens to be a large aggregation switch with hundreds of VLANs this could get pretty time consuming to create your template and double check your work. These are the types of scenarios where you will find creating a script with a modern scripting or programming language very useful. For right now I'm going to write a script in a fictional programming language called HumanScript to demonstrate how you may do this. 

But before we do this we are going to copy the output from the Juniper into a text file. Clean up that text file so you only have the VLAN data remaining. Then you will import that into excel and save it as a tab delimited text file. The reason you are going to use tab delimited instead of comma delimited is there are comma's in the Juniper output.

Now lets write our imaginary program in our imaginary programming langauage.

    read a line of the file
        separate each field and store it in variables name,tag,address,ports
        print "vlan $tag"
        print "name $name"
        for every port in the $port variable
                print "int g$x/$y"
                print "switchport"
                print "switchport mode access"
                print "switchport access vlan $id"
                print "all your fun dot1x and port security config"
                print "no shut"
        repeat for every port
    repeat all of above starting with the next line of the file


After you run this program you will have output creating the VLANs and the Switchport configs for the new switch.

If you are interested in seeing what this looks like in a couple of different real programming languages I've included links below.

[link to javascript code](https://github.com/natecriss/blog_code/blob/master/parse_vlan_txt.js)
[link to python code](https://github.com/natecriss/blog_code/blob/master/parse_vlan_txt.py)

Even though this is a lot better than doing it manually, doing things this way still kinda sucks. We will talk about why it sucks next time.
