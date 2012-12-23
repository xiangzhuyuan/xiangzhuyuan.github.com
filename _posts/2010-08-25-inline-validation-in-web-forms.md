---
title: Inline Validation in Web Forms
author: mathewxiang
layout: post
permalink: /2010/08/inline-validation-in-web-forms/
categories:
  - 默认
---
### [][1]

##### by [LUKE WROBLEWSKI][2]

<div style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; float: none; padding-top: 0px" id="scid:0767317B-992E-4b12-91E0-4F059A8CECA8:0097d2a5-a46b-4608-b6cb-6784fbfc3353" class="wlWriterEditableSmartContent">
  Technorati 标签: <a href="http://technorati.com/tags/jquery" rel="tag">jquery</a>,<a href="http://technorati.com/tags/ajax" rel="tag">ajax</a>,<a href="http://technorati.com/tags/asp.net+mvc" rel="tag">asp.net mvc</a>
</div>

from: <http://www.alistapart.com/articles/inline-validation-in-web-forms/>

*   Published in: [Scripting][3], [User Interface Design][4] 
*   [Discuss this article »][5]
    
    **|** [Share this article »][6]

![Inline Validation in Web Forms][7]

Web forms aren’t great conversationalists. They ask a bunch of questions, then wait until you answer them all before they respond. So when you register for that cool social network or use an e-commerce site, it’s pretty much a monologue.

You can blame most forms’ poor etiquette on the way they’re built. Web forms that use a basic submit-and-refresh model of interactivity don’t respond until you hit the “submit” button—but it doesn’t have to be this way. **<font size="4">Real-time inline validation can help people complete web forms more quickly and with less effort, fewer errors, and (surprise!) more satisfaction.</font>**

Inline validation gives people several types of real-time feedback: It can confirm an appropriate answer, suggest valid answers, and provide regular updates to help people stay within necessary limits. These bits of feedback can be presented before, during and / or after users provide answers.

#### Putting inline validation to the test

To better understand the design considerations behind inline validation, I worked with [Etre][8], a London-based usability firm, to test 22 average users on six variations of a typical web registration form. [Aramys Miranda][9] developed the form we used with our users, who ranged in age from 21 to 49.

![Basic registration form with no distractions][10]

Fig. 1. The basic registration form we tested had no distractions so people could focus on the task of “creating an account.”

Of our six forms, the control version validated input only when someone clicked its “create account” button. The other five versions used different methods of inline validation. We measured success rates, error rates, completion times, satisfaction ratings, and standard eye-tracking metrics for each variation. We presented each form randomly to minimize familiarity bias.

##### WHAT DID WE LEARN ABOUT INLINE VALIDATION?

Our participants were faster, more successful, less error-prone, and more satisfied when they used the forms with inline validation. Eye-tracking also showed that they “fixated” on the forms with inline validation less frequently and for less time, which shows that they found these forms easier to process visually than the forms without inline validation. This was likely because they didn’t have to reread the entire form after submitting it to resolve any errors—instead, they resolved errors as they went along.

As you can see in the video below, people got a response from the control version of the form only **after** they completed it to their satisfaction, and clicked the “create account” button. At that point, any errors were shown until the form was resubmitted. Submitting and resubmitting forms to check answers can lead to a form of the [frustrating and often unsuccessful behavior][11] sometimes called “pogosticking.” Pogosticking is common when we ask people to provide an answer they may not be able to guess correctly the first time. Selecting a unique username, for example, often involves pogosticking: no one can know beforehand which usernames a website has available, so they guess, click “create account,” find out the username they want is taken, guess again, click “create account,” again, and so on.

Video 1. The control version of our form. Note how error messages are only visible after the form is submitted.

Our inline validation forms worked differently: they gave real-time feedback as people filled in answers, using lightweight and direct success messages (green checkmarks) and error messages (red triangles and text) next to the form input fields. You can see the difference in Video 2 below.

Video 2. The best-performing version of our form used inline validation to provide real-time feedback immediately after people answered questions.

When compared to our control version, the inline validation form with the best performance showed compelling improvements across all the data we measured. Specifically, we saw:

*   a 22% increase in success rates, 
*   a 22% decrease in errors made, 
*   a 31% increase in satisfaction rating, 
*   a 42% decrease in completion times, and 
*   a 47% decrease in the number of eye fixations. 

Participant comments highlighted their strong preference for getting real-time feedback from our form:

*“You’d rather know about your mistakes as you go along.”*

*“It’s much better than getting all the way down and hitting ‘submit,’ only to find out that it doesn’t like your username. It’s much better when it tells you as you go along.”*

These results highlight how inline validation influences web forms. But what’s the best way to achieve these results? When and how should we validate user answers?

#### Use inline validation when the answers aren’t obvious

Not all web form questions are equal. There are some things, such as given names, that we know instantly. Other things, such as new passwords, take more thought. When you consider using inline validation, you must first understand the questions the form asks. This was evident in our test results.

In the first half of our web form, we asked questions people knew the answers to: first name, last name, e-mail address, gender, country, and postal code. In the second half of the form, we asked questions that were harder to answer correctly the first time. We had participants select a username (how could they know what was available?) and a password (with strict formatting requirements). It wasn’t surprising that we observed different behaviors in the first and second half of the forms.

Only 30%-50% of our participants saw the validation messages (Figure 2) in the first half of our forms—whereas 80-100% of our participants saw the messages in the second half. This is probably because people did not need or expect confirmation for correct answers in the first half of the form. Confident in their responses to these simple questions, most people paid no attention to the validation messages when they appeared.

![Validation messages on one of the forms we tested.][12]

Fig. 2. Validation messages on one of the forms we tested.

In contrast, in the second half of the form, when our participants completed more difficult questions (such as username and password), they were less confident in their answers and therefore more inclined to seek confirmation. Also, they were more likely to hesitate, giving them ample opportunity to spot the validation messages (including those already on display in the first half of the form). The eye-tracking gaze path below (Figure 3), illustrates this behavior. The validation messages to the right of the input fields got a lot of visual attention in the second half of the form but none in the first half.

![Visual attention mapping of validation messages.][13]

Fig. 3. Visual attention was paid to the inline validation messages that appear to the right of input fields in the second half of this version of the form.

These observations seem to indicate that inline validation is most useful for input fields that are difficult to complete easily. The fact that participants were confused when simple questions were marked “correct” supports this interpretation:

*“Are you telling me I entered a valid name or my name correctly?”*

*“Is this a confirmation of a correctly formatted postal code or my correct postal code?”*

These types of participant questions caused some minor problems during testing. Our participants knew we had no way to know their correct name or postal code, so they knew that the green check mark didn’t mean “correct.” But what did they think it meant? They weren’t sure—and that was the problem. Not knowing what the message meant, our participants stopped to ask questions of the moderator instead of confidently answering what were very easy questions.

We can blame the green check mark symbol that implies “correct,” for some of the confusion, but we also learned that we can avert this confusion altogether by reserving inline validation for questions people need help with. Inconsistency, however, may be the disadvantage of this approach. If success messages appear alongside every form field except for simple fields, people may assume the data they entered is invalid if no success messages appear. As a result, they may try to “correct” perfectly valid input in these fields. We’re not sure if this would be a big problem, but it’s certainly something to consider.

#### Testing when to show inline validation 

Once you know where inline validation can help, the next step is to put it into action. To better understand when to show inline validation messages, we tested a few variations in the top half of our form. (See Video 3 below.)

##### AFTER

In this version of the form, we displayed a validation message (success or error), after the user indicated that she was done answering a question by moving on to the next one. (This is validating “on blur” in technical speak.)

##### WHILE

In this variation, we displayed (and updated) a validation message while the user answered each question. (That is, “on key press.”)

##### BEFORE AND WHILE

In this version, we displayed a validation message before the user answered each question—that is, as soon as they focused each form element—and then **while** they answered the question. (This is validating “on blur and on keypress.”)

Video 3. The three inline validation variations we tested: after, while, and before and while.

For username and password questions, we used the “while” method with a short delay in each version we tested. Our early prototyping work revealed this method made the most sense for questions with strict boundaries, such as the set of usernames currently available or the required formatting for a secure password.

##### AFTER METHOD HELPS USERS TO COMPLETE FORMS MORE QUICKLY

When we used the “after” method in the first half of the form, participants completed the form seven to ten seconds faster than when we used the “while” and “before and while” methods respectively. Why? Here’s what happened when we used the “while” and “before and while” methods: When several participants noticed an error message while trying to answer a question, they entered one additional character into the input field, than waited for the message to update. If the updated message continued to show an error, they entered another character, then waited for the validation message to update again, and so on, resulting in longer average completion times.

The “before and while” method not only caused longer completion times, but also produced higher error rates and worse satisfaction ratings than the other inline validation variations we tested. Our participants articulated their strong distaste for this methodology:

*“It’s frustrating that you don’t get the chance to put anything in [the field] before it’s flashing red at you.”*

*“When I clicked in the First Name field, it immediately came up saying that [my first name] is too short. Well of course it is! I haven’t even started!”*

*“I found it quite annoying how red crosses came up when you hadn’t finished typing. It’s just really distracting.”*

These negative reactions, longer completion times, and error rates illustrate that validating inputs prematurely can be harmful. Instead, when you validate open-ended questions, give feedback *after* the user finishes providing an answer. Or in situations in which people need help sooner, give feedback *while* they work toward an answer, but use an appropriate delay so premature error messages don’t frustrate them.

#### Testing how to show inline validation

In each of the variations that tested *when* to show inline validation, we always placed success and error messages to the right of input fields. But to learn more about how to show validation messages, we also tested two additional variations: One where success messages faded after a brief delay and one that placed them inside the input field. In each version, the error messages faded only after the user resolved the error.

![Three variations of displaying validation messages][14]

Fig. 4. The three variations of displaying validation messages we tested.

Of these options, our participants fared best with persistent messages. These always-visible elements reassured participants that the fields they completed successfully stayed that way. As I mentioned earlier, though, we observed some confusion about the meaning of the green check mark: *Does it mean “correct” or “valid”?* As a result, you might try adding explanatory text (such as “complete” or “done”) to affirm success. You might also experiment with different validity indicators. This might prevent the confusion people had with the green check mark we used to represent correctness.

##### NOT FADE AWAY—KEEP SUCCESS MESSAGES PROMINENT OUTSIDE FORM FIELDS

When success messages faded away, some participants worried that they had done something to cause once-valid fields to become invalid. Persistent messages also enabled those who wanted to “check each field as they went” to do so, while accommodating those who wanted to ”check all of the fields at the end.”

We observed that fading messages were also easily missed because the vast majority of our participants were “hunt and peck” typists—as opposed to touch-typists—which meant that our users watched their fingers on the keyboard instead of the screen when entering data. As a result, they often missed messages that were on-screen for only a few moments.

Displaying validation inside form fields failed to deliver any substantial benefit. The positioning of these messages was—necessarily—inconsistent. (While it’s possible to make validation messages appear inside form fields, it is much more difficult to display them inside standard drop-down lists, so we displayed them outside these elements.) In-field validation was not any more noticeable than messages displayed outside the fields. In fact, the messages inside input fields were almost as far away from where people entered data as the other messages we tested (placed to the right of input fields). Had the messages been positioned closer to the inputs, they might have performed better.

##### THE RESULT: MUCH GAIN, LESS PAIN

Our testing provided some great insights. It also raised opportunities to more fully explore where, when, and how we should use inline validation to further alleviate web form pain so people can complete them and get to what they *really* want to do online. Which, trust me, isn’t filling in web forms!

##### THANKS

I’d like to thank [Etre][8] for all their work scripting, running, and reporting on this study and [Aramys Miranda][9], who coded all the variations we tested. ![][15]

*   Illustration by [Kevin Cornell][16]

 [1]: http://www.alistapart.com/articles/inline-validation-in-web-forms/
 [2]: http://www.alistapart.com/authors/w/lwroblewski
 [3]: http://www.alistapart.com/topics/topic/scripting/
 [4]: http://www.alistapart.com/topics/topic/userinterfacedesign/
 [5]: http://www.alistapart.com/comments/inline-validation-in-web-forms/
 [6]: http://www.alistapart.com/#shareLinks
 [7]: http://www.alistapart.com/d/inline-validation-in-web-forms/inline-validation.jpg
 [8]: http://www.etre.com/
 [9]: http://www.nexpace.com/
 [10]: http://www.alistapart.com/d/inline-validation-in-web-forms/figure1_540.png
 [11]: http://www.uie.com/articles/galleries/
 [12]: http://www.alistapart.com/d/inline-validation-in-web-forms/figure2_540.png
 [13]: http://www.alistapart.com/d/inline-validation-in-web-forms/figure3_540.png
 [14]: http://www.alistapart.com/d/inline-validation-in-web-forms/figure4_270.png
 [15]: http://www.alistapart.com/pix/eoai.gif
 [16]: http://www.alistapart.com/authors/c/kevincornell