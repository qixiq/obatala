# Questions API
## Concepts<br>
**obatala** - Runtime , libraries that can be reconfigured to build applications<br>
**None** - Empty structure<br>
**Identity** - Uniquely identifies an actor as known to obatala, not the same thing as user or human etc<br>
could be a usernanme/password maintained in obatala, or eg a Google or Facebook Login<br>
**Session** - {Captures information about Identity that is currently connected to obatala}<br>
**LoggedOnIdentity** {Session, Identity}<br>
**Question** - question to answer<br>
**QuestionAndAnswers** - a question to answer and mutiple choice answers to the question<br>
**QuestionTags** {Topics to which Question is related}<br>
**Anwser** {Related to a Question}<br>
**QuestionHistory** - A sequence of Questions and results related to a LoggedOnIdentity<br>
**Maybe<Concept>** - A structure that may contain a related Concept or nothing eg asking a question may return an answer or nothing<br>
<br>
## Actions<br>
**Login** - Call this method to establish a session<br>
~~~

Request
GET /login?userName=<user-name>&password=<password>   -- Will currently accept any non-empty string for userName, and password is userName123.

Response
 - Success {"isError":false,"sessionId":"df9e2929-74a4-4557-ace3-607e8dbdca22","error":null} //sessionId is unique for every Login
 - Failure {"isError":true,"sessionId":null,"error":{...}}
~~~


**GetQuestion**- Call this method to obtain a new question for the LoggedOnIdentity<br>
~~~
Request
GET /getquestion?sessionId=<sessionId> - sessionId obtained from earlier call to login

Response
 - Success 
 {
      "isError":false,
      "questionAndAnswers":
      {
        "question":"What is the Capital City of Niger?",
        "questionId":"34adf2bc-faf4-4188-8c76-aa3195131b7c",
        "answers":
        [
            {"choiceAlphabet":"A","answer":"Minna"},
            {"choiceAlphabet":"B","answer":"Umuahia"},
            {"choiceAlphabet":"C","answer":"Bauchi"},
            {"choiceAlphabet":"D","answer":"Yola"},
            {"choiceAlphabet":"E","answer":"Kano"}
        ]
      },
      "error":nul
}
 - Failure {"isError":true,"questionAndAnswers":null,"error":{...}} 
~~~


**GetAnswer** - Call this method to get the answer to a question<br> 
~~~
GET /getanswer?sessionId=<sessionId>&questionId=<questionId>&answer=<A|B|C|D|E> - sessionId obtained from earlier call to login, questionId obtained from earlier call to getquestion

Response
 - Success {"isError":false,"answered":"**true**","error":null} //if <answer> in request in correct letter
 - Success {"isError":false,"answered":"**false**","error":null} //if <answer> in request in NOT correct letter
 - Failure {"isError":true,"answerd":false,"error":{...}}  
~~~
