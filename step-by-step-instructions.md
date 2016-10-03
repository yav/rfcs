Fork the RFC repository from GitHub
-----------------------------------

The RFC repository is located at:

    https://github.com/haskell/rfcs

To fork it, go to the above URL and click on the `Fork` button in the
top-right corner of the page.  This will create your own copy of the repository
on GitHub.  For example, for me this new repository is located at:

    https://github.com/yav/rfcs

You only need to do this once.


Making a Proposal
-----------------

In the examples in this section I will use `USER` for the GitHub user,
and `FEATURE` for the name of my the new feature I am proposing.
You should replace `USER` with your GitHub user name, and `FEATURE` with
some name suitable for the feature being proposed.

  1. Download `000-template.rst` to your computer
      1. Go to: `https://github.com/USER/rfcs`
      1. Click on the file `000-template.rst` in the root directory of the repo
      2. Click on the `Raw` button in the top right
      3. Save the resulting file somewhere on your computer,
         using the name `0000-FEATURE.md`

  2. Fill in the template on your computer, explaining the proposed feature.

  3. Upload the proposal back to GitHub and make a pull request:
      1. Go to: `https://github.com/USER/rfcs`
      2. Create a new branch for the proposal:
         1. Click on the "current branch" button (top left, says something
            like `Branch: master` and has a little down arrow on it).
         2. Type in the name of the new branch in the text box
            (e.g. FEATURE)
         3. Press `Enter`.  Now the current branch button should say
            `Branch: FEATURE`.
      3. Click on the directory called `texts` in the repo.
      4. Click on the `Upload files` button (top right)
      5. Click on the `choose your files` link (or drag files as the page says), and select `0000-FEATURE.md` from your computer.
      6. Write `FEATURE` in the `Commit changes` text box
      7. Make sure the radio box is on the
        `Commit directly to the FEATURE branch.`
      8. Click on the green `Commit changes` button.
         Now you should be back on the main page for the repo, and the
         current branch should still say `Branch: FEATURE.
      9. Click on the `New pull request` button
          (next to the current branch button).
      10. Click on the green `Create pull request` button
      11. Optional: check that everything worked:
          1. Go to: `https://github.com/haskell/rfcs`
          2. Click on the `Pull requests` tab (top, 3rd from the left).
          3. You should see your pull request there.
          4. Click on your pull request.
          5. Click on `Files changed` (there should be 1 of thse).
          6. You should see a diff with your proposal in it.











