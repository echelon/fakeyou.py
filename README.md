# FakeYou.py
# Author IG : @thedemonicat
**FakeYou.py** is a Python module that helps you to use [FakeYou](https://fakeyou.com/) API
with simple functions and some featuers.

## Note
This is **beta version**, it may be buggy and slow

## Documentation!

i'll explian every **function** and **Error handling** thing you need so you have as smooth as possible programs with it!

Let's Start!

### Calling the main class:
The main class have 2 arguments
- proxies : type = dict, use them to avoid IP ban, default is **None**
- verbose : type = bool, set it True to make the program more talktiv, default is **False**
```
import fakeyou
proxies={
    "http":"host:port"
    "https":"host:port"
}
fy=fakeyou.FakeYou(proxies=proxies,verbose=False)
```
### get all the categories/voices:
have one argument that **size**, it decides how much it should return, when its setted to 0, it will return everything, default= **25**

```
import fakeyou 

fy=fakeyou.FakeYou()

voices=fy.list_voices(size=100)
```
`FakeYou().list_voices()` returns 13 diffrent list, you can handle it with zip, example:
```
import fakeyou

fy=fakeyou.FakeYou()

voices=fy.list_voices()

for title,creator in zip(voices.title,voices.creatorUsername):
	print(title,creator)
```
and here's the lists:
- modelTokens 
- ttsModelType 
- creatorToken
- creatorUsername
- creatorDisplayName
- creatorGavatarHash
- title
- langTag
- isFrontPageFeatured
- isTwitchFeatured
- categoryTokens
- created
- lastUpdate
- json

and goes the same for categories:
```
import fakeyou

fy=fakeyou.FakeYou()

categories=fy.list_voice_categories()

for name,token in zip(categories.name,categories.categoryToken):
	print(name,token)
```
and here's categories lists:

- categoryToken
- modelType
- maybeSuperCategoryToken
- canDirectlyHaveModels
- canHaveSubCategories
- onlyModsApply
- name
- dropDownName
- isModApproved
- created
- lastUpdate
- deleted
- json


### search function
it have one argument, and its query, you just put what you want to search
```
import fakeyou

fy=fakeyou.FakeYou()

result=fy.search("mario")

for title in result.voices.title:
	print(title)

for name in result.categories.name:
	print(name)
```

function **search** returns 2 objects, voices and and categories

### say function

this is a function that generates TTS in a specfic voice model 
it have 3 args, ttsModelToken, text, and filename

- text : is the text to convert to speech
- ttsModelToken : voice model token
- filename : the filename that stores the sound, by default its "fakeyou.wav"

```
import fakeyou

fy=fakeyou.FakeYou()

fy.say(text="Hello im mario",ttsModelToken="TM:7wbtjphx8h8v")
```


## Error handling

there's only 3 errors

- TooManyRequests
- RequestError
- TtsAttemptFailed

```
import fakeyou

fy=fakeyou.FakeYou()

try:
	fy.say(text="Hello im mario",ttsModelToken="TM:7wbtjphx8h8v")
except fakeyou.exception.TooManyRequests:
	print("Cool down")
```
## Error handling example ^


### how to deal with them?

- well TooManyRequests error because your ip has been banned for a couple of minutes because you were spamming requests, you can use proxy or just wait

- and RequestError better contact me 

- TtsAttemptFailed is because you maybe used an unsupported language or a wrong token, just check what you have used.