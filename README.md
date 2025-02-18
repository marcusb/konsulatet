# konsulatet

Fork of [@danielnorberg's script](https://github.com/danielnorberg/konsulatet)
to scrape the web site of the Massachusetts Registry of Motor Vehicles (RMV) for appointments.

## Usage

1. Get a https://www.twilio.com/ trial account, get a twilio phone number & verify the phone number you want to send sms to
2. `brew install maven` (if you don’t have maven + java)
3. `git clone git@github.com:marcusb/konsulatet.git`
4. `cd konsulatet`
5. `TWILIO_SID=badf00d TWILIO_TOKEN=badf00d NOTIFICATION_NUMBERS=+12222222222,+13333333333 TWILIO_NUMBER=+14444444444 ./run.sh`
6. Verify that you get the hello world SMS on startup, otherwise something is wrong and you might not get any notifications for appointments.

* The `TWILIO_SID`, `TWILIO_TOKEN` env vars should be set to your twilio SID and auth token.
* `TWILIO_NUMBER` should be your assigned Twilio phone number.
* `NOTIFICATION_NUMBERS` Can be one or more comma separated numbers to send SMS to. Note that the numbers must be verified in your Twilio account.

## Note

* The application checks for open appointments at all RMV offices.
* The `run.sh` script tries to run the application forever and restart it on crash.
* An SMS is sent if the application crashes so you can debug and get it up and running again.
* SMS are throttled to not notify more than once an hour for the same office. To clear the throttle: `rm -rf sms-sent`.
* Headless Firefox is used via selenium. You need to have Firefox installed.
