## Live Demo 

https://earthchie.github.io/Firebase-CRUD-Example/

http://earthchie.com/firebase/crud/ (Thai language interface)

#### Rules
```json
{  
   "rules": {  
      ".read": true,
      ".write": "auth != null",
        
      "Entry": {  
         ".read": true,
         ".write": "auth != null",
           
         "$child": {  
            ".read": true,
            ".write": "auth != null",
              
            "views": {
               ".read": true,
               ".write": true,
               ".validate": "data.val() == null || newData.val() == data.val() || newData.val() == data.val()+1"
            }
         }
      }
   }
}
```
This rule allows guest to increase number of views, while protect them from editing something else.

Let's break down this line
```json
".validate": "data.val() == null || newData.val() == data.val() || newData.val() == data.val()+1"
```

``data.val() == null`` is allow to create.

``newData.val() == data.val()`` is allow to update with the exact same value.

``newData.val() == data.val()+1`` is allow to increase value by 1.

## License
WTFPL 2.0 http://www.wtfpl.net/
