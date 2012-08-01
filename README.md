track
=====

ultra-lightweight version control

Track was written so that I didn't have to have to install git (or rcs) onto test machine
that would would be reinstalled in fairly short order, but that I was developing code on. Git was 
too heavyweight, and rcs is just kind of painful to use and still a bit heavy. Since the machine would
have a full python installation, I decide to write a simple version tracking system in pure python.

Track leaves out everything I didn't need. No users. No client-server. No branching. No file locking. 
`track` is for one user working on one thing. It works by copying whole files into a hidden directory.
It keeps track of comments in a json file. It does a few clever diffs, and lets you examine the repository.

And that's pretty much it. It's not a collaboration tool, like git or perforce. It's just a very simple version 
tracker.

to use:

    >ls
    foo bar bang
    >track foo bar bang  #start tracking the files
    >track -r #list the repo
    bang
    foo
    bar
    >vi foo #change foo
    >track -d foo #diff the file
    --- /Users/stillson/track/track/test/.track/foo.01
    +++ foo
    @@ -1,1 +1,2 @@
    asdf
    +asdf
    
    >track foo #check in the current version
    >track -d foo #this is now empty
    
The basic usage is `track filename` copies a new revision into the repository if the file has changed.

`track -d filename` diffs with the last check in.

There are more options. Read the code :)