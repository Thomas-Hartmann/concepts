# python
- [Editor](###-Editor)
- [Anaconda](###-Anaconda)
- [Libraries](###-Libraries)
- [Collections](###-Collections)
- [Best practises](###-best-practises)
- [Comments and documentation](###-Comments)
- [Regular Expressions](###-Regexp)
- [Files and folders](###-Files)

### Editor
1. editor: VSCodium
2. ipython and ipython notebook
3. build-ins
    - __name__
    - __doc__ : documentation in beginning of document `"""some doc here"""`
4. setup.py building the project to restructure the whole project.

5. install tree
6. install anaconda (with python)

codewith.mu - online editor for python for beginners.
pygame.org - online til at lave spil.

7. http.server start og se alle filer i mappen.
8. library numpy
9. django for 

### Collections
List, Tuple, Dictionary
#### Comprehensions
capitalsDict = {"paris":"France", "London":"England","Lisbon":"Portugal"}
reverseKeyValueDict = {capitalsDict[key]:key for key in capitalsDict} //Will return {"France":"Paris",...etc..}

### NamedTupple
- Named tuple is used to find value by a name instead of a numeric index.
- `Person = collections.namedtuple('Person', 'name age gender')` and `bob = Person(name='Bob', age=30, gender='male')`  
- 
### Anaconda
- Create a virtual environment for installs: `conda create -n exercises` and `source activate exercises` to start up the environment.
- When conda environment is running -> install module: `conda install -c conda-forge pyperclip` conda-forge was necesary. conda-forge is a conda repository with many packages to install.

### Comments
And documentation.
- Documentation: first line in function or class or module is written as documentation string with triple quotes: `"""bla bla bla """` (tripple quotes is used for multiline string).

### Idioms (best practises)
https://en.wikibooks.org/wiki/Python_Programming/Idioms

### Regexp
ONLINE tester: https://pythex.org/
- `\n` backslash is used to escape charaters
- `raw text` is text that does not need escaping eg.
  - `'\\d\\d\\d-\\d\\d\\d-\\d\\d\\d\\d'` vs
  - `r'\d\d\d-\d\d\d-\d\d\d\d`
- `import re` to work with regular expression.
- `phoneNumRegex = re.compile(r'\d\d\d-\d\d\d-\d\d\d\d')` phoneNumRegEx is the regex object.
- `search()` is a method on the regex object
  - `matchFound = phoneNumRegex.search(someString)` 
  - `matchFound.group()` matchFound.group() will be the actual phone number that was found.
  - Test a particular pattern on a text online: [**http://
regexpal.com/**](http://
regexpal.com/)
- `groups()` use groups to get a tuple of alle matching strings
- `group(0)` all parts of the first match
- `group(1)` first part of parenthes match `re.compile(r'(\(\d\d\d\)) (\d\d\d-\d\d\d\d)')` eg `415` of match `415-333-6545`. Notice how `\(` looks for an actual parenthes.
- pipe `|` is used for `OR` like: `re.compile(r'frog|toad')` will match either frog or toad and return the first one found.
- ex: `re.compile(r'(frog|toad)leg')` to find either frogleg og toadleg.
- `findall()` instead of search() will find all occurences.
- `re.compile(r'Bat(wo)?man')` a question mark here means 'wo' is optional
- `phoneRegex = re.compile(r'(\d\d\d-)?\d\d\d-\d\d\d\d')` the first 3 digits are optional. 
- `(\d)*` zero or more times with a digit when postfixing an asterix.
- `(\d)+` one or more times when postfixing a plus.
- `(\d){3}` only match 3 digits exactly
- `(hi ){3,5}` matches 'hi hi hi' and  'hi hi hi hi' and 'hi hi hi hi hi'
- `(hi ){3,5}?` with a question mark we get the shortest possible match rather than the default longest match. 'hi hi hi' rather than 'hi hi hi hi hi'.

|short hand character| description|
|---|----|
|\d| Any numeric digit from 0 to 9.|
|\D| Any character that is not a numeric digit from 0 to 9.|
|\w| Any letter, numeric digit, or the underscore character. (Think of this as matching “word” characters.)|
|\W| Any character that is not a letter, numeric digit, or the underscore character.|
|\s| Any space, tab, or newline character. (Think of this as matching “space” characters.)|
|\S| Any character that is not a space, tab, or newline|

- use `^` caret symbol to match only the start of the string: `r'^Hello'` will mathc 'Hello you' but not 'Say Hello from Me'.
- use `$` to match the end of the string
- user `^` and `$` to match string exactly: `wholeStringIsNum = re.compile(r'^\d+$')`.
- use wildcart `.` to match any charactor that is not a new line.
```
atRegex = re.compile(r'.at')
atRegex.findall('The cat in the hat sat on the flat mat.')
['cat', 'hat', 'sat', 'lat', 'mat']
```
- Match any and all things: `.*` dot= any char and star=zero or more of them.
- `re.compile('.*', re.DOTALL)` will match new lines as well.
- IGNORE CASE: `re.compile(r'robocop', re.I)` or `re.IGNORECASE` 

- Substitute text.
```
namesRegex = re.compile(r'Agent \w+')
namesRegex.sub('CENSORED', 'Agent Alice gave the secret documents to Agent Bob.')
'CENSORED gave the secret documents to CENSORED.
```
- Making complex rexexp readable: 
```
phoneRegex = re.compile(r'''(
(\d{3}|\(\d{3}\))?             # area code
(\s|-|\.)?                     # separator
\d{3}                          # first 3 digits
(\s|-|\.)                      # separator
\d{4}                          # last 4 digits
(\s*(ext|x|ext.)\s*\d{2,5})?   # extension
)''', re.VERBOSE)
```
- Use `|` pipe character to give more parameters to the compile() function: `someRegexValue = re.compile('foo', re.IGNORECASE | re.DOTALL | re.VERBOSE)` since compile only accepts one parameter.

### Files
Read and write to files and folders.
- `import os`
- `os.getcwd()` get current working directory
- `os.makedirs('new-dir-name')` creates a new directory in cwd
- `os.chdir('existing-dir-name')` changes current working directory to the one requested
- `os.path.abspath('.')` returns the absolute path of a relative path.
- `os.path.getsize('/home/thomas/desktop/somefile.txt')` returns the size of a file
- ``
- ``
- ``