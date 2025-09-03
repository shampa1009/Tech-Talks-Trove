🚦CAP Theorem in System Design
Ever wondered why distributed systems always feel like a balancing act?

⚡We can’t have it all. We can only pick 2 out of 3. A distributed system cannot simultaneously guarantee:
🔹Consistency (C) → Every read reflects the latest write.
🔹Availability (A) → Every request gets a response.
🔹Partition tolerance (P) → The system works even if the network splits.

👉 In reality, partitions are inevitable, so when they happen, we must pick:
🔹CP (consistency + partition tolerance) → Accurate but may reject requests (e.g., banking systems).
🔹AP (availability + partition tolerance) → Always responsive but may serve stale data (e.g., social feeds, shopping carts). 
Stale data is information that is no longer accurate or current because it has not been updated to reflect the latest changes.

💡Daniel Abadi introduced the pacelc theorem to fill the gap:
✅p → if there is a partition → System chooses between A (availability) or C (consistency).
✅else (e) → when the system is running normally → We must choose between L (latency) and C (consistency).
👉 hence the name: p-a-c-e-l-c

💡Why pacelc matters
In reality, partitions are rare, but latency vs consistency trade-offs happen all the time.
🔸pacelc forces us to consider:
 ① Do we return results fast (low latency) but risk stale data?
 ② or, Wait for more replicas to agree (high consistency), but slower responses?

📌CAP highlights what happens during failures, but pacelc extends the thinking: even when everything is working, we’re still trading off latency vs consistency. Real-world systems like DynamoDB (low latency by default, C optional) and Spanner (consistency, higher latency) show these choices in action.

📌 Don’t just memorize CAP. In interviews or real-world design, show you can reason about the trade-offs, when correctness matters more, when responsiveness wins, and how to adapt designs in between.

 👇 If you were designing a shopping cart service, would you favor availability (AP) so users never lose an “add to cart” action, or consistency (CP) to ensure totals are always 100% accurate?

#SystemDesign #TechInterviews #CAPtheorem #AlexXu #DistributedComputing #SoftwareEngineering #LinkedInLearning
