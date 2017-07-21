This project is the uncompiled source for the Apache Rya website.
Branch master is this source in markdown for the Jekyll tool.
Branch asf-site is the compiled HTML that is deployed to the webserver.
To make changes to the website:

1. Git clone git://git.apache.org/incubator-rya-site.git branch master
2. Created a new branch.        git checkout -b your_new_branch_name_here
3. install Jekyll.  This may not be straight forward if you don't have a ruby environment.  You may have to add Linux distro packages, then ruby gems, then more packages as dependendencies present themselves. 
4. Modify the markdown as needed using a text editor.
5. New releases go in folder _posts along with other news.
6. Releases must use the prescribed file naming format and have a header variable catagories=release along with some other variables describing the version.
7. The download.md should automatically populate based on your new post file and its variables, but it may need tweaking.
8. Run this command to auto-compile and web serve on port 4000:
    bundle exec jekyll serve
9. Now just iteratevly use your editor and web browser to edit and test changes.
10. When you are done making changes:
11. Move the content/target folder out of the way, you will commit this separately.
12. Commit changes to your own public git repo.
13. Create a pull request to the repo apache/incubator-rya-site branch master.

14. Now for the deployable HTML that you moved above:
15. In the same git folder, 
    git checkout --force origin/asf-site 
    git checkout -b another_new_branch_name_here
    rm -r content/*
Note: --force removes any stray files left over.
Note: replace another_new_branch_name_here with a new branch hinting at your changes.
Note: the recursive remove of all the content is nessary to discover files deleted as well as changed.
16. Now copy the folder formally named target/ into the project renamed to content/.
17. Use git status to observe changes.  The css and other template files are probably not changed.  If they are flagged as modified, investigate CRLF or other trival differences.  See .gitattributes.
18. When done, commit to your repo in a new branch as above.
19. Create a pull request as above, except to be merged into branch asf-site.
20. Beg and bribe peers and mentors to review changes.
21. Make changes and commit them as above.  No need to create new pull requests as they follow the latest commit in the branch.

