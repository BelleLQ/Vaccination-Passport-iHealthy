# Vaccination-Passport-iHealthy 
Prototype Link:
https://www.figma.com/proto/EJR1Y7btRqPcb9JtEjY2ki/iHealthy?node-id=0%3A1

<img width="458" alt="Screen Shot 2021-05-26 at 3 07 47 PM" src="https://user-images.githubusercontent.com/59607658/119717308-2566c100-be34-11eb-9c0a-2ccd85b52382.png">

# Background
As we all know, COVID-19, an unexpected global pandemic, is still hovering around the globe in 2021. Countries are locked down, the economy is cut off, but life must go on. Thanks to our researchers and scientists, several effective vaccinations are produced in such a short time, and there will be more coming out. We are confident with our government that our society and economy will be returning to normal, and the pandemic will be ending. Now in Canada, residents are taking vaccinations in stages. We can expect our life will soon be the same way as normal.
# Problem
Vaccine recipients in Canada are given paper receipts in the current system. When I have this receipt, I am vaccinated, and I am free of COVID-19 virus, which means this paper is a health passport. It is not an effective way to bring this paper receipt every day, and it is difficult for others to verify it.
For residents waiting for their vaccinations, they are facing the risks of exposure to COVID-19 virus in common areas. If they are exposed to a person who is to be tested positive, then they have a high probability that they are infected, but the fact is that they don't know, and no one knows.
When we acknowledge that someone has a high probability of infection, we need to commit a COVID test. And probably we may take COVID test on a regular basis. We have to take the test reports with us to show that we are tested negative and we are safe to enter common areas. This is not a convenient and effective way.
Since vaccination is taking in stages, our normal life, shopping malls, retails, office buildings, and all common areas will be reopening in stages. In common areas where all residents are vaccinated, we don't need to wear masks at all times because the probability of our risk of having COVID-19 is very low. It will be an effective way to check the vaccination status or recent COVID test status before entering a common area.
# Goal
Our mobile app is designed with the idea of protecting our users' privacy and safety in the first place. And we add more features to make our app more convenient and accessible in multiple scenarios. Our app aims to help the public return to normal with lower concerns on exposure to COVID.
This app will be securely tracking the users whether they have close contact with people who may be tested positive for COVID in the next 14 days. If the user is potentially exposed to COVID, then notifications will be sent to remind them of taking a COVID test.
Additionally, the most important part of our app is to keep track of the users' COVID test and COVID vaccination history. Effective vaccinations will be treated as a health passport for the public to reopen confidently. Therefore, our app generates a QR code with a color system to identify the health passport quickly and securely.
# User Analysis
## Target Users
Our app is providing services to all Canadian residents whose personal health information is logged to the current health system.
We have taken multiple scenarios into consideration: users who are entering a building, stores, schools, companies, public transportations, etc. where the facility requires a health passport condition as entrance permission.
With considerations of residents who do not have access to a smartphone and who have difficulties with using a smartphone, and in specific scenarios, our app is able to use NFC technology to simplify the process of verifying the passport.
## User Needs
With privacy deeply in our mind, our app provides a secure solution to help the public return to normal. We understand and take our users needs into our considerations:
1.	Government and unauthorized institutions have no access to the users' personal health privacy.
2.	Effective notification if users are in close contact with persons who are tested positive.
3.	Time scheduler and reminder if vaccination needs a scheduled booster.
4.	Convenience and quick access as a health passport and avoid long verifying procedures.
# Technical Requirements
## Database Design and Connection
The users' COVID test records and vaccination records are securely stored on the Cloud. When we need to present our QR code, our app will send the users' identification, which can be one of SIN, Health Card number, or Driver License number, the Cloud will match our identification so that we can fetch the COVID test ID and Vaccination ID. Based on these records, our app will automatically generate a QR code with a color system, which can be presented to the verifier. In this way, the verifier has no access to our detailed test reports but only brief information.
<img width="468" alt="image" src="https://user-images.githubusercontent.com/59607658/119718983-3d3f4480-be36-11eb-8c52-b33965eb1d27.png">


# Distance Tracking - Apple & Google Exposure Notification
To prevent the spreading Covid virus, social distancing is the most important measure of protection. Instead of tracking the users' location by GPS, our app tracks the distance between devices to protect privacy.
The distance tracking technology we can apply is Apple Exposure Notification, which is a framework developed by Apple and Google. This framework is specified as Privacy-Preserving Contact Tracing. This API is using a new Bluetooth protocol to detect the distance between devices, and it is used in the governments' COVID tracing app.
## Benefit of using Exposure Notification:
1.	Protect users' privacy. This technology is not collecting location data but only detecting distance. And the random identifier of the user is changing every 15 minutes. Users' privacy is highly safeguarded.
2.	Lower energy consumption. New Bluetooth technology consumes lower energy than GPS. This feature decreases the probability that the users will turn off the app for saving the battery.
# Apple Wallet API
Apple Wallet is a mobile app developed by Apple with iOS. We can use the API to build our digital health passport on Apple Wallet. Our app will generate a QR code for displaying the health status, and this code can be integrated into Apple Wallet for flexible access.
Benefit of using Apple Wallet:
1.	Convenient to show the QR code of the health status. Opening the app and waiting for the QR code to show up is time consuming. Apple wallet offers another way to open our QR code.
2.	Protect our privacy. Opening the app has the chance of tapping the personal health information button, then there will be risks of exposing personal health information in public.
## Apple Near Field Communication (NFC) API
Apple NFC technology enables devices to communicate and exchange information with each other in close contact wirelessly. NFC technology is widely used for Apple Pay, keycards, etc.
### Benefit of using NFC:
1.	NFC reading machines are widely used in many scenarios, such as PRESTO card reading machines, buildings access doors. Existing reading machines can read our app after proper program modification.
2.	Reduce the risk of exposing the QR code in public. If your QR code is often exposed in the public for verification, then there is a risk that others may take the photo of your code.
3.	Safe and fast connection. NFC technology is secure to connect and exchange information. The connection between devices is fast so if many people pass into a place, we will save our users' time.
# Functional Analysis
## COVID Tests Record & Vaccinations Record
To make sure the test results are authentic, when our users take COVID tests in a hospital, the test results will be updated by the hospital staff. Users only have permission to view the test results. If our user has more than one test results, the latest result will be used as a criterion for deciding the risk level a user has.
After our users are vaccinated, the hospital staff can update the information of this vaccination, including vaccinating date, vaccine booster, and company. A user can accept several vaccinations, the records will be saved in our database. The vaccination record is a criteria to get a green level pass in this app.
## Contact-Tracing
Contact-Tracing is an important weapon to prevent COVID from spreading. The Exposure Notification technology requirements and advantages are introduced above. We will use this technology to keep track of the user's distance from other devices.
1.	The user's smartphone will generate random Bluetooth identifier keys every 15 minutes. Random changing keys are to protect the user's privacy.
2.	Other devices within social distance will receive the broadcasting from the user's Bluetooth and exchange identifier keys with each other. The identifier will be stored locally to protect the users' privacy.
3.	If the user is tested positive, and the user agrees to input the result to the Vaccination Cloud, then the user's past 14 days Bluetooth identifier keys will be uploaded to the Cloud.
4.	If other users match with the keys correctly, then they will receive a notification by text message, email, and app notification. Multiple notifications are to ensure they will receive our notice properly.
5.	Users who receive notice will be advised to have a COVID test, and their QR code and the color system will be changed accordingly.
## Health Passport System
### QR Code
Similar with barcode but more powerful, QR code is widely used because of its fast readability and high data storage ability. QR codes can be instantly recognized by smartphone cameras within 2 seconds, which makes it convenient for health passport verification.
Our app will fetch data from the Vaccination Cloud and COVID Test Cloud, and a QR code that contains these information is generated automatically. This code will be updated every time when users open the app, and will be refreshed after a certain period of time. This is to avoid people sharing pictures of their QR codes.
### Color System
Our app's color system is as simple as green, yellow, and red. Based on the most recent COVID test result and the vaccination status, our users' QR code and system theme color will be classified by colors.
In our design, green color means the user has been fully vaccinated; red color means the user is tested positive or contact closely with someone who is tested positive; other scenarios will become yellow color. Color will be automatically refreshed based on the most updated data from the Cloud. Since COVID test results and vaccination records can only be modified by authorized clinics and institutions, the user will have access to modify the QR code or to change the color system.
<table>
<tr>
  <th>Color</th>	
  <th>Health Status</th>
</tr>
<tr>
  <td>Green</td>	
  <td>Fully Vaccinated</td>
</tr>
<tr>
  <td>Red</td>	
  <td>User is tested positive or contact closely with someone who is tested positive, except they are fully vaccinated</td>
</tr>
 <tr>
  <td>Yellow</td>	
  <td>Any other situations</td>
</tr> 
 </table>
### Apple Wallet & NFC Tap-N-In
Our app will be able to generate the QR code in the Apple Wallet. The QR code and color system will be synced with the app. Once agreed by the user, it will be added into the Apple wallet, then it can be used in the same way as in our app. This is to save our users' time on opening apps.
Additionally, our app will introduce NFC technology to combine with the existing equipment at the entrances of buildings. With NFC technology, the app will transmit users’ health status into the equipment of NFC receivers quickly and securely. This saves our users' time from unlocking and opening apps.
# Business Case
## Contact-Tracing Case
Example for Contact-Tracing Refer to Apple:
 <img width="197" alt="image" src="https://user-images.githubusercontent.com/59607658/119718111-2cda9a00-be35-11eb-9afa-85bab67fe984.png">
1.	User Amy and user Bob closely contacted each other in a common area. There smartphones exchange a random identifier key via Bluetooth, and the key will be stored locally.
2.	User Amy is tested positive for COVID-19 two days later, and Amy agrees the test results to be input to the Vaccination Cloud
3.	The Vaccination Cloud updates the database, and Amy's smartphone will upload identifier keys within the past 14 days to the Cloud.
4.	The Vaccination Cloud will notify users whose identifier key matches with Amy's. User Bob receives notifications and is suggested to take a COVID test, and Bob's health passport status is updated.
## QR code and color system case
Example for QR code and color system:
<img width="468" alt="image" src="https://user-images.githubusercontent.com/59607658/119718054-1e8c7e00-be35-11eb-8429-1805fe000191.png">
1.	The Vaccination Cloud is exchanging data with our app, and the health passport keeps updated
2.	The verifier will scan the QR code or by verifying the color of the QR code to simplify the process.
3.	Based on the facility's policy, the verifier will approve or reject the access.
## Office building access
Example for using normal access card to buildings:
 <img width="468" alt="image" src="https://user-images.githubusercontent.com/59607658/119718042-16ccd980-be35-11eb-9b6b-fe1e85ef7ac6.png">
1.	The Vaccination Cloud is exchanging data with our app, and the health passport keeps updated
2.	The Office building local cloud stores the employees' unique user ID, though which the office building acknowledges the health passport status of the employees.
3.	The Office building will update the availability of the employees' access card to the building based on the employees' health passport status.
4.	Employees will use their access card to the Office building as normal. Their normal working life is not influenced or delayed by verifying the health passport status.
# Application Prototype

## Competitor Analysis
### Current Competitors
As this global pandemic develops, many governments, companies, and individuals are proposing their solutions to COVID notification apps.
1.	CoronaMelder is a coronavirus notification app. CoronaMelder uses Bluetooth to detect nearby people who have the same app on their phones. The app will notify the user if the user has been near someone for more than fifteen minutes who turns out to be tested positive.
2.	SwissCovid is a contact tracing app. SwissCovid anonymously measures the time and distance the user is with another's smartphone, and records those which are getting closer than 1.5 meters for longer than 15 minutes in a day. When a user is tested positive for the coronavirus, the app will warn the users who have encountered the infected people in the period of the starting two days before the first symptoms occur.
### Our Advantage
Besides using Bluetooth to detect the distances and contact time between the users as mentioned above, our app also has QR code and NFC tap-n-in features. With these two features, our app provides a convenient key to the facilities.
1.	With our QR code feature, the verifier can easily verify the visitors’ health status before letting them enter. The records of visitors can also be used to alert users when there is a visitor tested positive. Besides, our QR code is refreshing every time when we re-enter the app and when the code is displayed for a certain time.
2.	The usage of NFC provides an alternative method for verifiers to verify visitors’ health status. NFC scanners are currently used in many buildings. With this feature, they don’t need to purchase new devices to get the information from this app but only to properly program their current devices.
3.	Our color system as described above provides a clearer and faster way to easily identify the users' health status. We can save time scanning our green code which means securely vaccinated persons once the verifier sees the green code.
# Future Upgrades
1.	Using smartwatches will be a convenient way to verify the health passport. We will build a simplified app based on watchOS for Apple Watch, only accessible to necessary information, and sync to the app on the smartphone.
2.	The color system can be updated to a more reasonable and complete layer system to cover application scenarios as complete as possible. So the verifier can easily tell which layer of users are allowed to enter the area or not.
3.	Integrate with the current healthcare system. Users will have access to their own personal health history from their family doctors, clinics, and hospitals. Online appointments booking, online meetings with doctors, and other features can be added.
4.	Digital health card. We can integrate a chip to the current Ontario health card if the person does not have access to a smartphone or it's difficult for them to learn to use a smartphone. The chip should be able to securely read and write by authorized institutions.
5.	Smartphone face ID verification. In case sharing smartphones and making fake records, every time when accessing our health passport, we will verify the user's face ID, and match the record in the vaccination cloud.
6.	Camera face ID verification. In places having higher security requirements, we can integrate a real-time face recognition technology and match the face recorded in the vaccination cloud.
7.	Blockchain technology can be used to securely handle the user's contact history, COVID tests and vaccination reports history.
