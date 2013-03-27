[PHPixie](http://www.phpixie.com) - PasswordHash ([PHPass](http://www.openwall.com/phpass/))
=====================
About
---------------
**PasswordHash** is a PHPixie Module-structured extension that gives the ability to use PHPass's hashing functions
in your PHPixie project.

Usage
---------------
The usage is exactly the same as the original PHPass:

1. Add the *PasswordHash* folder into your PHPixie's `application/modules/` folder
2. Configure `application/config/core.php` `modules` array with the name of the module
3. Instantiate the `PasswordHash` class (`parameters => log_2_(int x), portable_hash(bool y)`)
4. Use the instance to hash or check a password:

        $hasher = new PasswordHash(8, false);
        
        $original = "hello world";
        $original_hash = $hasher->HashPassword($original);
        
        $userinput = "hello world";
        
        $check = $hasher->CheckPassword($userinput, $original_hash);
        
        if($check)
        {
          echo "Password is Correct!";
        }
        else
        {
          echo "Password is Wrong! :(";
        }
