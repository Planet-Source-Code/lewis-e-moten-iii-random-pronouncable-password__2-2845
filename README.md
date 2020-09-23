<div align="center">

## Random Pronouncable Password


</div>

### Description

Allows client browser to randomly create a pronouncable password. This can be used to suggest a password to the user that is easy to remember.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Lewis E\. Moten III](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/lewis-e-moten-iii.md)
**Level**          |Beginner
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |
**Category**       |[Security](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/security__2-74.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/lewis-e-moten-iii-random-pronouncable-password__2-2845/archive/master.zip)

### API Declarations

```
<SCRIPT src="RandomPassword.js"></SCRIPT>
<SCRIPT>
for(var i=0;i<25;i++)
{
document.write(RandomPassword(7,10) + '<BR>');
}
</SCRIPT>
```


### Source Code

```
function RandomPassword(Min, Max)
{
	var password = new String('');
	var addConsonant = new Boolean(true);
	var doubleConsonants = new String('cdfglmnprst');
	var singleConsonants = new String('bcdfghjklmnprstv');
	var letter = new String('');
	var vowels = new String('aeiou');
	var length = new Number(0);
	var index = new Number(0);
	length = Math.round(Math.random() * (Max - Min)) + Min;
	while (password.length < length)
	{
		random = Math.round(Math.random() * 100);
		// 10% Double Consonants
		if(password != '' && addConsonant && random < 10)
		{
			index = Math.round(Math.random() * (doubleConsonants.length - 1));
			letter = doubleConsonants.substring(index, index+1);
			password += letter + letter;
			addConsonant = false;
		}
		else
		{
			// 80% Consonants
			if(password != '' && addConsonant && random < 90)
			{
				index = Math.round(Math.random() * (singleConsonants.length - 1));
				letter = singleConsonants.substring(index, index+1);
				password += letter;
				addConsonant = false;
			}
			// 10% vowels
			else
			{
				index = Math.round(Math.random() * (vowels.length - 1))
				letter = vowels.substring(index, index+1);
				password += letter;
				addConsonant = true;
			}
		}
	}
	if(password.length > Max)
	{
		password = password.substring(0, Max)
	}
	return(password)
}
```

