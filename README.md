# Apache Rya Web site source

This project is the markdown version of the official Apache Rya website.
This project is processed by Jekyll and committed to the asf-branch.
- Branch master (you are here) is this source in markdown for the Jekyll tool.
- Branch asf-site is the compiled HTML that is deployed to the webserver.

## Modification

To make changes to the website:

1. Git clone git://git.apache.org/incubator-rya-site.git branch master
2. Created a new branch.        

    ``git checkout -b your_new_branch_name_here``

3. Modify the markdown as needed using a text editor.
4. New releases go in folder _posts along with other news.
5. Releases must use the prescribed file naming format and have a header variable catagories=release along with some other variables describing the version.
6. The file download.md, using its scripts, should automatically populate the coresponding html based on your new post file and its variables, but it may need tweaking.

7. Install Jekyll.  This may not be straight forward if you don't have a ruby environment.  You may have to add Linux distro packages, then ruby gems, then more packages as dependendencies present themselves. 

8. Run this command in the content/ folder to auto-compile and web serve on port 4000:

    ``cd content/``
    
    ``bundle exec jekyll serve``

9. Now just iteratevly use your editor and web browser to edit and test changes.
10. When you are done making changes:
11. Move the content/target folder out of the way, you will commit this separately.
12. Commit changes, add a remote to your own public git repo, and push to it with --set-upstream.
13. Create a pull request to the repo apache/incubator-rya-site branch master.
14. Now for the deployable HTML that you moved above:
15. In the same git folder, 

    ``git checkout --force origin/asf-site 

    git checkout -b another_new_branch_name_here

    rm -r content/*``

Note: --force removes any stray files left over.

Note: replace another_new_branch_name_here with a new branch hinting at your changes.

Note: the recursive remove of all the content is necessary to discover files deleted as well as changed.

16. Now copy the folder formally named target/ into the project, renaming it to content/.
17. Use git status to observe changes.  The css and other template files are probably not changed.  If they are flagged as modified, investigate CRLF or other trival differences.  See .gitattributes.
18. When done, commit to your repo in a new branch as above.
19. Create a pull request as above, except to be merged into branch asf-site.
20. Beg and bribe peers and mentors to review changes.  Consider hosting the site temporarily for review, see below.
21. Make changes and commit them as above.  No need to create new pull requests as they follow the latest commit in the branch.


## Hosting for review on Github pages

1. Review the setup here:  https://pages.github.com/  using "project-site"
2. It doesn't mention it in the quick start above, but it will also publish a site from a branch named "gh-pages" which is important since master is already used for another purpose.
3. Start with your branch of project "incubator-rya-site" as pushed to your remote, that is based on the asf-site branch.
4. Create and checkout a new branch named "gh-pages".  This will not be used in a pull request.

    ``git checkout -b gh-pages``
    
5. Move the contents of the "content" folder to the root of the project.
6. Modify each HTML page prepending to all references (href= and src=) to the site with "/incubator-rya-site" .  Ignore references beginning http.

For example:

    Before:
    
        ``<link href="/assets/themes/apache/bootstrap/css/bootstrap.css" rel="stylesheet">``
        
    After:
    
        ``<link href="/incubator-rya-site/assets/themes/apache/bootstrap/css/bootstrap.css" rel="stylesheet">``


This command should do the replacement:

    ``find . -name \*.html -exec sed -ri 's/=\"\//=\"\/incubator-rya-site\//g' {} \;``


7. Commit changes and push to your public github project named incubator-rya-site.

    ``git commit -a -m "New stuff"``
    
    ``git push  git push --set-upstream yourGitHub gh-pages``
    
8. Login to your github account and to the project incubator-rya-site forked from apache/incubator-rya-site, and click on the Settings tab.  Scroll down to GitHub Pages  and choose source=gh-pages branch.  Save.
    
9. Browse to the site:

    https://yourGitHubID.github.io/incubator-rya-site
    
replacing yourGitHubID with your GitHub account ID.

10. Check your work and ask others to review by sending this URL.



