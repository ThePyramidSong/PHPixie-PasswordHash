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
3. Instantiate the `PasswordHash` class (`parameters => log_2_iters(int x), portable_hash(bool y)`)
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

*PasswordHash* (constructor) Parameters
---------------------------
This class holds a constructor that asks for two parameters:

* **Base 2 Logarithm iteration count**: it will decide by how much `2` will be raised for, and thus how many iterations will the algorithm do.
        A good number for this parameter is between **7** and **12**. Remember that the iteration count increases rapidly depending on this number
        and eats lots of CPU power (good for hashing security, but beware...)
* **Hash Portability**: provides hashing portability for really old servers. Leave it always on *false* unless you truly need that compatibility.

*HashPassword* (method) Parameters
-----------------------
This method hashes the password and just asks for one parameter:

* **String to Hash**: self-explanatory. No need to salt. You'd just like to escape it first, and check for injections.

*CheckPassword* (method) Parameters
-------------------------
This method compares two strings:

* **Raw String to Compare With**: the raw (non-hashed nor salted) string to compare. Again, escape and make it safe.
* **Hashed String to Compare To**: the hashed string, probably saved in your database.

And it returns a simple **boolean** :)
