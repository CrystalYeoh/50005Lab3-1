# Define required macros here
REMOVE = rm
CC = gcc


# Explicit rules, all the commands you can call with make 
# (note: the <tab> in the command line is necessary for make to work) 
# target:  dependency1 dependency2 ...
#       <tab> command

#Called by: make targetname 
#also executed when you just called make. This calls the first target. 
all: rootprogram rootdoprogram logaccessprogram rootprogram_nosuid setup 

rootprogram: rootprog.c
	$(CC) rootprog.c -o rootprog

rootdoprogram: rootdo.c
	$(CC) rootdo.c -o rootdo 

logaccessprogram: logaccess.c 
	$(CC) logaccess.c -o logaccess 

rootprogram_nosuid: rootprog.c 
	$(CC) rootprog.c -o rootprog_nosuid

# refresh the root files and root log file
# Set UID for rootprog and rootdo
# Set logaccess to be executable only by ROOT
setup: 
	chmod 744 logaccess 
	chmod u+s rootprog 
	chmod u+s rootdo
	echo THIS IS ROOT FILE > rootfile.txt
	echo THIS IS ROOT FILE > rootlogfile.txt

test:
	ls -la
	./rootdo ./logaccess testlogFile
	cat rootlogfile.txt

clean:
	$(REMOVE) rootprog
	$(REMOVE) rootdo 
	$(REMOVE) logaccess 
	$(REMOVE) rootprog_nosuid
	$(REMOVE) rootfile.txt
	$(REMOVE) rootlogfile.txt

