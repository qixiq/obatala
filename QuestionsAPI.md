# Questions API
## Concepts<br>
**obatala** - Runtime , libraries that can be reconfigured to build applications<br>
**None** - Empty structure<br>
**Identity** - Uniquely identifies an actor as known to obatala, not the same thing as user or human etc<br>
could be a usernanme/password maintained in obatala, or eg a Google or Facebook Login<br>
**Session** - {Captures information about Identity that is currently connected to obatala}<br>
**LoggedOnIdentity** {Session, Identity}<br>
**Question** - question to answer<br>
**QuestionTags** {Topics to which Question is related}<br>
**Anwser** {Related to a Question}<br>
**QuestionHistory** - A sequence of Questions and results related to a LoggedOnIdentity<br>
**Maybe<Concept>** - A structure that may contain a related Concept or nothing eg asking a question may return an answer or nothing<br>
<br>
## Actions<br>
LoggedOnIdentity **Logon**(Identity) - Call this method to establish a session<br>
Question **GetNewQuestion**(LoggedOnIdentity) - Call this method to obtain a new question for the LoggedOnIdentity<br>
QuestionHistory **GetQuestionHistory**(LoggedOnIdentity) - Call this method to get a collection of questions that were already asked of this LoggedOnIdentity<br>
Answer **GetAnswer**(Question) - Call this method to get the answer to a question<br>
None **AddQuestionAndAnswer** (LoggedOnIdentity, Question, Answer) - Call this method to add a new question and answer<br>
Maybe<Answer> **AskAQuestion**(LoggedOnIdentity, QuestionText (a string)) - Free form question asked, may or maynot return an answer<br>
