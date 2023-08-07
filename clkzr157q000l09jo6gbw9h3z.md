---
title: ""Shebang - #!" : A Beginner's Guide to the Shebang in Shell Scripting"
datePublished: Sun Aug 06 2023 18:00:11 GMT+0000 (Coordinated Universal Time)
cuid: clkzr157q000l09jo6gbw9h3z
slug: shebang-a-beginners-guide-to-the-shebang-in-shell-scripting
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691341808827/a47d7ed8-89ae-4e48-9cd3-39d0bc53dbd3.png
tags: linux, bash, learning, shell-scripting, 90daysofdevops

---

**Introduction**

If you've ever come across a shell script, you might have noticed this line at the beginning that reads "`#!/bin/bash`." This symbol "`#!`" is known as the "shebang," and it holds significant importance in the world of shell scripting. It is a line of code that tells the operating system which program to use to execute the script.

**How Important Is #!/bin/bash?**

A shell script's shebang line is always the first line. It instructs the operating system on which script interpreter to utilize. In this instance, "`/bin/bash`" denotes the system's location for the Bash interpreter.

You can access Bash-specific features, extensions, and syntax by specifying "#!/bin/bash," which may not be available in other shells. Bash has a wide range of features, including arrays, string manipulation, and more, that may be used to create shell scripts that are robust and adaptable.

**Can we also write #!/bin/sh?**

Yes, you can also write `#!/bin/sh` as well. The `/bin/sh` is a Bourne shell, a simpler shell than bash, and can be accessed via the `/bin/sh` path. If you enter `#!/bin/sh`, the Bourne shell will run the script.

However, using `#!/bin/bash` as opposed to `#!/bin/sh` is generally advised. This is so because Bash, as opposed to the Bourne shell, has more functionality and is more popular. Your scripts will be more adaptable and functional on a larger number of platforms if you develop them in Bash.

**Example**

```plaintext
#!/bin/bash

# This script compares two numbers and displays the result.

# Require user input
read -p "Enter the first number: " num1
read -p "Enter the second number: " num2

# Compare the numbers
if [ $num1 -eq $num2 ]; then
    echo "Both numbers are equal."
elif [ $num1 -gt $num2 ]; then
    echo "First Number ($num1) is greater than Second Number ($num2)."
else
    echo "Second Number ($num2) is greater than First Number ($num1)."
fi

echo "I will complete #90DaysOofDevOps challenge"
```

**How to Execute the Script?**

1. Save the script in a file, [`compare.sh`](http://hello.sh).
    
2. Make the script executable: `chmod +x`[`compare.sh`](http://compare.sh).
    
3. Run the script: `./`[`compare.sh`](http://compare.sh)