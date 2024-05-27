
## RULES COMMANDS
## Append a rule

iptables [--table table-name] --append chain-name matching-criteria --jump target

## Delete a rule
iptables [--table table-name] --delete chain-name matching-criteria --jump target

## Insert a rule 
iptables [--table table-name] --insert chain-name [rulenum] matching-criteria --jump target

## replace an existing rule 
iptables [--table table-name] --replace chain-name rulenum matching-criteria --jump target

## show the content of a chain
iptables [--table table-name] --list [chain-name]

## empty a chain 
iptables [--table table-name] --flush [chain-name]

## To create a user-defined chain

iptables [--table table-name] --new-chain [chain-name]

