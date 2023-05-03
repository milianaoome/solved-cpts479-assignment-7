Download Link: https://assignmentchef.com/product/solved-cpts479-assignment-7
<br>
For this homework you will extend the QuizApp functionality from HW5 so that for each quiz question you will have the option to schedule a local notification for that question. I have posted my solution to HW5 on Blackboard Learn. You can work from this version, or your own. See screenshots below. Specifically,

<ol>

 <li>We will need to uniquely identify a quiz question other than by its index in the quiz array. Add a “uniqueId” String property to the Question class and set it to “UUID().uuidString” when the question is first created. This id string is guaranteed to be unique.</li>

 <li>In the View Question view add a “Schedule Notification” button at the bottom of the view. When this button is tapped, the app should first generate an alert asking you to confirm the scheduling of a notification. If canceled, then nothing happens. If confirmed, the app should schedule a notification to appear in five seconds and pop the view back to the table view. The notification title should be “Question of the Day” and the notification body should be the quiz question prompt. The notification userInfo dictionary should contain the quiz question’s uniqueId so that when the app gets the didReceive message, it will know which quiz question was in the notification.</li>

 <li>In the Quiz table view controller of the app, implement a handleNotification method that will be called from the AppDelegate when the user has opened the notification. This method should extract the uniqueId from the notification response and search the quiz array for the question with the uniqueId. If the question still exists (it might have been deleted), then the app should segue to the View Question view for this question. If the question does not exist, then the app stays in the Quiz table view.</li>

 <li>In the AppDelegate, conform the class to the UNUserNotificationCenterDelegate protocol. In the didFinishLaunchingWithOptions method request authorization to receive notifications and set the user notification center delegate to self. You may assume the user initially allows notifications and does not disable them at any point.</li>

 <li>Also in the AppDelegate class, add the didReceive UNUserNotificationCenter delegate method. This method should first ensure that the app is in the table view, not the View question view or the Add Question view. This can be done by checking if the navigationController.topViewController is of the type of the table view controller; if it is</li>

</ol>

1 not, then the app should pop this view. Then the app should call the handleNotification method in the Quiz table view controller class with the notification response.

<ol start="6">

 <li>Be sure that auto layout constraints are set so that the view elements are appropriately displayed with no overlap regardless of device orientation.</li>

 <li>Other than the changes described above, your app should also meet all HW5 requirements.</li>

</ol>




StoryBoard: