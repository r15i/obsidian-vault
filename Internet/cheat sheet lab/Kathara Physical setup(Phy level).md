
# Scripting Physical 
**lab.conf** is the file describing the network topology and it's physical structured of the collision domains as :

**\<NAME_OF_THE_MACHINE\>**\[ **NUMBER_OF_THE INTERFACE** \] =**\<NAME_CO_DOM\>**


(exist other [[tags for lab.conf|tags]] for more specific  porposes)
### Example of lab.conf
LAB_DESCRIPTION="Description of the lab"
LAB_VERSION=1.0
LAB_AUTHOR="Emilio Risi"
LAB_EMAIL= laboratori@dei.unipd.it
pc1[0] = A 
pc2[0] = A
pc2[1] = B
pc3[0] = B

# Standalone Scripts Physical 

## Start a new machine 

kathara **vstart** -n **pc1** **--eth 0:A**

- **pc1** sets the name of the machine 
- **0:A** sets the number  of the interface (**0**) and the name of the collision domain (**A**)
## kill a machine 

kathara **vstart** -n **pc1** 
- kills the the pc with name pc1


