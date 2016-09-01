Live Demo http://earthchie.com/firebase/crud/

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

``data.val() == null`` = allow to create.

``newData.val() == data.val()`` = allow to update with the exact same value.

``newData.val() == data.val()+1`` = allow to increase value by 1.
