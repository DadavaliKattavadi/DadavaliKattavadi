- 👋 Hi, I’m @DadavaliKattavadi
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
DadavaliKattavadi/DadavaliKattavadi is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
trigger SendWelcomeEmailOnAccountCreate on Account (after insert) {
    for (Account acc : Trigger.new) {
        Messaging.SingleEmailMessage mail = new Messaging.SingleEmailMessage();
        String[] toAddresses = new String[] {acc.Email};
        mail.setToAddresses(toAddresses);
        mail.setSubject('Welcome to Our Company!');
        mail.setPlainTextBody('Dear ' + acc.Name + ', \n\n Welcome to our company! We are excited to have you as a customer. \n\n Best regards, \n Your Company Name');
        Messaging.sendEmail(new Messaging.SingleEmailMessage[] { mail });
    }
}
