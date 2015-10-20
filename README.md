##Hashcat Rules Reference
I often find myself looking up hashcat rules on the 
<a href="http://hashcat.net/wiki/doku.php?id=rule_based_attack">hashcat website</a> and one day I thought it would be 
easier just to have all possible rules and their explanations/examples in one .rule file but commented out. That way, 
whenever I need to use a rule I just open it up and uncomment the rule that I want.

The purpose of a rules file is to modify (or permutate) every word in a wordlist. Imagine you had a wordlist that 
looked like this...

abc<br>
def<br>
xyz<br>

And you wanted to test permutations of those words such as abc123, cba, aabc, ABC, etc. For every permutation you want 
to make you write one rule on one line. For example, if you wanted to uppercase every word in your list your rules file 
would look like this...

u

This would cause ABC, DEF, and XYZ to be tested. You can also combine multiple rules on the same line. If your rules 
file looked like this..

u$1

It would first uppercase the word (ABC), then append 1 to the end so it would test ABC1, DEF1, XYZ1 and so on.

If you save the `hashcat_rules.txt` file to your hashcat folder you can use it like this...

oclHashcat64 -m 2500 -r hashcat_rules.txt CAP.hccap WORDLIST.txt

I find having a textual description of the rule right in the rules file makes it much easier to look up what rules do 
what.
