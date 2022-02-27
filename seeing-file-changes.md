# Seeing File Changes

You can use the command line or another tool to view files that have changed. VSCode has a great diff tool.

```bash
echo stuff > c.txt

git add .

git commit -m "your message here"

echo things > c.txt

# shows that c.txt was changed, "stuff" was removed, and "things" was added
git diff
```
