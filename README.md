this is just exercise that i did when learning fullstack engineer at codecademy. therefore, the whole code wasnt mine. i only put a few lines to complete exercise

goal of this exercise is to apply what i've learn abt preventions for SQL injection attacks.

what i've done in this exercise:

ADDING VALIDATOR
1. at the top of app.js, add require the validator package:
const validator = require('validator');

VALIDATING THE WEB FORM

2. create if statement in callback function that is in /track route (code that handle form submission for customer info) that check if the input is integer: 
if(validator.isInt(req.body.customerId))
3. and then if the input is not integer, send error by create else statement:
res.json({
  "message": "Invalid customer ID."
});

PREPARED STMT IN BACKEND CODE

4. use prepared statement for the sql query in the /track route's if stmt so that they are not constructed directly from the form submission:
db.all(
      `SELECT * FROM Employee WHERE EmployeeId = $customerId`, {
        $customerId: req.body.customerId
      }, (err, rows) => {...}
    );
