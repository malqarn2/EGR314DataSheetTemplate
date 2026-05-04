# Reflection

## Review of Module's Success

Looking back at my module requirements, I was able to complete the main goals of my light subsystem. I successfully built the subsystem around the ESP32-S3, connected the light sensor, and used the ADS1115 ADC to read the sensor as a 16-bit value. I was also able to create working UART communication that could send and receive packets using the class packet format. In addition, I updated my API page and message documentation so my subsystem messages matched the team communication structure.

One of the biggest successes was getting the light subsystem to correctly detect light and convert that reading into a simple status value of 1 or 0. This made it easier to communicate useful information to the rest of the team. I was also able to test packet framing, forwarding, and message handling, which helped prepare the subsystem for checkoff and final integration.

At the same time, there were some requirements that were more difficult than expected. One challenge was debugging communication because sometimes problems came from wiring, sometimes from packet formatting, and sometimes from code logic. Another challenge was making sure my GitHub datasheet matched what the team was actually using, since the protocol changed over time. I also spent a lot of time making sure my board would send the right message format and that the sensor threshold worked correctly. Overall, I think I completed the most important goals, but I learned that documentation and integration can take almost as much effort as building the hardware itself.

## Microcontroller/Module Startup Tip

One tip I would give to students starting their module is to test one thing at a time. Do not try to build the whole project at once. First make sure the board powers on correctly. Then test one LED. Then test UART. Then test the sensor. This makes it much easier to find the real problem when something goes wrong.

Another important tip is to verify pin assignments very early. A lot of time can be lost if TX and RX are reversed, or if the pins in the code do not match the real board connections. It is also helpful to print debugging information often, especially raw UART data and sensor values. Seeing the actual values on screen helps a lot when you are trying to figure out whether the problem is hardware or software.

I also learned that it is very important to understand the packet format before writing too much code. If the team changes the message structure later, it can force you to rewrite a lot of your work. It is better to confirm the exact bytes, sender IDs, receiver IDs, prefix, suffix, and message types before finalizing your code. Another tip is to keep your code simple at first. Start with a small working version, then add more features after the basic communication works.

## Lessons Learned

One of the most important things I learned from this project is that debugging embedded systems takes patience. A problem can come from hardware, wiring, power, software, or documentation, and sometimes more than one problem exists at the same time. I learned that it is important to test carefully and not assume the issue is only in one place.

I also learned that communication protocols must be very clear. Even small confusion about sender IDs, receiver IDs, or message formatting can break the whole system. Because of this, I learned to pay close attention to exact byte order and exact packet structure.

Another lesson I learned is that documentation matters a lot. At first I thought the main work would only be building the subsystem and writing code, but I found that keeping the GitHub datasheet accurate was also very important. If the documentation does not match the real behavior, integration becomes difficult for everyone.

I learned how useful external ADCs can be when a sensor needs more precise readings. Using the ADS1115 helped me understand how analog data can be read, converted, and then simplified into useful output for the rest of the system.

I also learned the importance of thresholds in sensor systems. My light sensor could produce a range of values, but the system often needed a simple yes-or-no answer. Choosing a good threshold was necessary to make the subsystem reliable.

Another lesson was that packet framing is critical. Prefix and suffix bytes make it possible to detect where a message starts and ends, which becomes very important in UART communication. Without proper framing, it is easy for data to be misread or dropped.

I learned that forwarding messages is just as important as handling messages for yourself. In a daisy-chain system, each board has to help the whole chain work, not just its own subsystem. That changed the way I thought about communication design.

I also learned that visible debugging tools are very helpful. LEDs, print statements, and simple test scripts can save a huge amount of time. Sometimes a small debug step tells you more than trying to guess the problem.

Another important lesson was that team coordination is necessary. Even if one subsystem works by itself, it still has to match the rest of the team system. I learned that asking for clarification early can prevent a lot of confusion later.

Finally, I learned that building a working project is not just about finishing the code. It is also about making sure the subsystem can be tested, explained, demonstrated, and integrated with others. That was probably the biggest lesson from the entire class.

## Recommendations for Future Students

1. Start early and test each subsystem feature one at a time instead of trying to finish everything at once.

2. Make sure you understand your packet format and team IDs before writing too much communication code.

3. Use print statements, LEDs, and small test scripts often because they make debugging much easier.

4. Keep your GitHub datasheet updated as the project changes so your documentation always matches your real hardware and code.

5. Communicate with your teammates often, because many project problems come from mismatched assumptions rather than from hardware alone.
