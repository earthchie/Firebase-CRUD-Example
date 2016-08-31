Live Demo http://earthchie.com/firebase/crud/

## Rules ที่ใช้
```
{
  "rules": {
    ".read": true,
    ".write": "auth != null",
    
    "Entry":{
      
    	".read": true,
    	".write": "newData.hasChildren(['views']) || auth != null"
      
    }
  }
}
```
