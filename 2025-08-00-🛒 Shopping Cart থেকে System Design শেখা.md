🛒 Shopping Cart থেকে System Design শেখা

ধরুন আপনি cart এ shoes add করলেন এবং refresh দিতেই item উধাও!
এটা আসলে bug না, design trade-off.

এখানেই আসে CAP theorem আর Consistency models.

1️⃣ Consistency Models
🔸Strong consistency (linearizability): Always latest write - like একটাই database আছে মনে হবে (zookeeper, hbase).
🔸Serializability: সব transaction serial order এ হচ্ছে মনে হবে (SQL).
🔸Eventual consistency: একদম সাথে সাথে না, but শেষমেশ সব replica sync হয়ে যাবে (DNS, Dynamo).
🔸Causal/session consistency: আপনার নিজের action order maintain হবে, কিন্তু অন্য user হয়ত আলাদা দেখবে।

2️⃣ Quorum system – tuning the knobs 🎛️
Distributed DB তে:
🔸N = Total replicas
🔸W = কতগুলো node write confirm করবে
🔸R = কতগুলো node read confirm করবে
👉 rule: W + R > N → strong consistency
example:
🔸N=3, W=2, R=2 → fresh data
🔸N=3, W=1, R=1 → fast but stale possible

3️⃣ Shopping cart & CAP trade-offs
🔸AP (availability + partition tolerance): সবসময় add/remove possible, but cart কখনো stale দেখাবে.
🔸CP (consistency + partition tolerance): সবসময় correct, but partition হলে update reject হতে পারে।
💡 ecommerce generally করে - browsing এ availability, আর checkout এ consistency.

4️⃣ Real-world Databases
🔸DynamoDB (AWS): Default AP, checkout এ strong read option.
🔸Cassandra: Tunable consistency (ONE, QUORUM).
 🔹ONE → Fast adds during browsing.
 🔹QUORUM → Fresher reads at checkout.
🔸MongoDB: শুরুতে AP, এখন transactions → CP support করে।

 📌System design মানে trade-off choose করা.
 📌Cart browse করতে চাইলে speed > accuracy.
 📌Checkout এ চাই accuracy > speed.

❓ আপনি shopping cart design করলে availability বেছে নেবেন নাকি consistency?

#SystemDesign #TechInterviews #CAPtheorem #AlexXu #DistributedComputing #SoftwareEngineering #LinkedInLearning
