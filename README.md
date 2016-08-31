Live Demo http://earthchie.com/firebase/crud/

#### Rules
```json
{
  "rules": {
    ".read": true,
    ".write": "auth != null",
    
    "Entry":{
    	".read": true,
    	".write": "auth != null",
        
        "$child":{
            ".read": true,
    		".write": "auth != null || (newData.hasChildren(['views']) && !newData.hasChildren(['title']) && !newData.hasChildren(['content']) && !newData.hasChildren(['createdAt']) && !newData.hasChildren(['updatedAt']) && !newData.hasChildren(['author']))",
      }
        
    }
      
  }
}
```
This rule is not perfect, but satisfied the objective of this repository. I'll find the better way to improve these rules soon.