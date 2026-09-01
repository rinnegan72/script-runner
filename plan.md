# Script Runner
This is a tool, built as a hobby project. The goal is to recreate atuin scripts function
in a custom tool, make it more like the warp terminal workflows funciton

## My issues with atuin script run
1. requires either interactive or fixed variable run commands
ie. I want a nvim style template autofil option, instead of environment=production or prompted
I want a drop down list I can pick available options from
2. interactive scripts
atuin can't handle interactive scripts requiring that I use pbcopy to copy a gereated command and run it
this adds a small lag in my existing workflow
3. sensitive env
I want either infisical or some other way to get env than just having it in the script

## How to do this?
Language Candidates: Bash, Rust, Go Lang
**Bash**: can call every tool I want, will work accross systems without adaptations
**Rust**: it is what atuin is written in
**Go Lang**: good for learning

**Basic logic from atuin's docs**
1. Get interpreter from config block
2. Create a full text document with the required substitutions (terra blocks `{{}}` with actual values)
3. Create a temp file with the rendered text
4. Spawn a Command::new interpreter with the interpreter from step 1
5. Capture the output

**New Logic**
1. to 4. copied from atuin, 2. modified to accept option list
5. Don't capture the output or do it in a way that accounts for it being interactive
