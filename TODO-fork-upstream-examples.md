# TODO: Fork Upstream Examples Repo

## Problem
The current `moku-examples` submodule approach is causing issues:
- Submodule reference errors (`fatal: remote error: upload-pack: not our ref`)
- Complex sparse-checkout configuration that needs manual intervention
- Unwanted directories still appearing despite sparse-checkout
- Hacky workarounds in `runme.sh` that are fragile

## Solution: Fork and Maintain Minimal Version

### Why This Approach is Better
1. **Reliability**: No more submodule headaches
2. **Performance**: Much faster clones and updates
3. **Control**: Full control over what content is included
4. **Maintenance**: Easier to manage and update
5. **Team Collaboration**: Others can clone your minimal version directly

### Implementation Steps

#### Phase 1: Create Minimal Fork
```bash
# Clone the original repo
git clone https://github.com/liquidinstruments/moku-examples.git
cd moku-examples

# Create a new minimal repo
mkdir ../moku-examples-minimal
cd ../moku-examples-minimal
git init

# Copy only what you need
cp -r ../moku-examples/python-api ./
cp -r ../moku-examples/mcc ./
cp ../moku-examples/README.md ./
cp ../moku-examples/LICENSE ./

# Create .gitignore to exclude unwanted content
echo "matlab-api/" > .gitignore
echo "neural-network/" >> .gitignore
echo "other-language-api/" >> .gitignore
echo "*.pdf" >> .gitignore
echo "*.md" >> .gitignore
echo "!README.md" >> .gitignore

# Initial commit
git add .
git commit -m "Initial minimal moku-examples with only VHDL and Python content"

# Push to your fork
git remote add origin https://github.com/YOUR_USERNAME/moku-examples-minimal.git
git push -u origin main
```

#### Phase 2: Update Workspace
1. Remove existing submodule from current workspace
2. Replace with direct clone of your minimal fork
3. Update `runme.sh` to remove submodule complexity
4. Test that everything works correctly

#### Phase 3: Clean Up
1. Remove all submodule-related code from `runme.sh`
2. Remove `.gitmodules` file
3. Update documentation to reflect new approach
4. Commit all changes

### Benefits After Implementation
- ✅ No more submodule reference errors
- ✅ Faster workspace setup
- ✅ Cleaner, more maintainable codebase
- ✅ Full control over included content
- ✅ Easier for team members to get started

### Maintenance
- Set up periodic sync with upstream repo when needed
- Can cherry-pick specific updates or improvements
- Full control over what gets included/excluded

## Priority: HIGH
This will eliminate ongoing maintenance headaches and improve developer experience significantly.

## Notes
- Consider naming the fork something like `moku-examples-minimal` or `moku-vhdl-python-examples`
- Make sure to preserve commit history or at least attribution to original authors
- Test thoroughly before removing old submodule approach
