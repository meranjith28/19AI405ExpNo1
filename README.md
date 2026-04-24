<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name:  RANJITH G</h3>
<h3>Register Number: 212224060209</h3>


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h3>Theory</h3>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>Medicine prescribing agent</strong></td>
    <td><strong>Treating unhealthy, agent movement</strong></td>
     <td><strong>Rooms, Patient</strong></td>
    <td><strong>Medicine, Treatment</strong></td>
    <td><strong>Location, Temperature of patient</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>
```
import random

class MedicinePrescribingAgent:
    def __init__(self):
        self.performance = 0
        self.current_room = 1  # Agent starts in Room 1

    def sense(self, patient_temp):
        """Sense if patient is healthy or unhealthy based on temperature."""
        if patient_temp > 98.5:
            return "unhealthy"
        return "healthy"

    def treat(self, patient_status):
        """Treat patient if unhealthy."""
        if patient_status == "unhealthy":
            print(f"Patient is unhealthy. Prescribing medicine ✅")
            self.performance += 10
        else:
            print(f"Patient is healthy. No treatment needed.")

    def move(self):
        """Move agent to the other room (reduces performance)."""
        self.current_room = 2 if self.current_room == 1 else 1
        self.performance -= 1
        print(f"Agent moved to Room {self.current_room} (performance -1)")

    def run(self, rooms):
        """Run the agent in the environment (rooms with patients)."""
        for _ in range(2):  # Two rooms to check
            patient_temp = rooms[self.current_room]
            patient_status = self.sense(patient_temp)
            print(f"Agent in Room {self.current_room} | Patient temp = {patient_temp}°F → {patient_status}")
            self.treat(patient_status)
            self.move()

        print(f"\nFinal Performance Score: {self.performance}")


# --- Simulation Environment ---
# Random patient temperatures in 2 rooms
rooms = {
    1: round(random.uniform(97, 101), 1),  # Room 1 patient temperature
    2: round(random.uniform(97, 101), 1)   # Room 2 patient temperature
}

print("Hospital Environment (Rooms with patient temperatures):")
print(rooms, "\n")

# Create and run agent
agent = MedicinePrescribingAgent()
agent.run(rooms)```
# OUTPUT
<img width="644" height="320" alt="Screenshot 2025-09-30 103143" src="https://github.com/user-attachments/assets/6d11c4b2-deb5-49db-aadd-2bd154eaa058" />
