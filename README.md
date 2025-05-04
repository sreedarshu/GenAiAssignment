import random

def get_prescription(symptom, severity):
    prescriptions = {
        "fever": {
            "mild": "Take Paracetamol 500mg every 6 hours and drink plenty of fluids.",
            "moderate": "Take Paracetamol 650mg and monitor temperature. Consult a doctor if it persists.",
            "severe": "Seek immediate medical attention. IV fluids and stronger medication may be required."
        },
        "headache": {
            "mild": "Take Ibuprofen 200mg if needed and get some rest.",
            "moderate": "Take Naproxen 250mg and avoid screen exposure.",
            "severe": "Consult a neurologist. Might require a stronger painkiller like Sumatriptan."
        },
        "cough": {
            "mild": "Use a cough syrup like Benadryl and drink warm water frequently.",
            "moderate": "Use Dextromethorphan syrup and take honey with warm tea.",
            "severe": "Visit a doctor. Possible need for antibiotics like Azithromycin."
        },
        "cold": {
            "mild": "Take Vitamin C supplements and use steam inhalation.",
            "moderate": "Use an antihistamine like Cetirizine and a decongestant.",
            "severe": "Consult a doctor. Possible flu requiring antiviral medication."
        },
        "stomach pain": {
            "mild": "Take an antacid like Pantoprazole before meals.",
            "moderate": "Avoid spicy foods and take Omeprazole 20mg.",
            "severe": "Severe pain could indicate ulcers or appendicitis. Seek immediate medical attention."
        }
    }
    return prescriptions.get(symptom.lower(), {}).get(severity.lower(), "Please consult a doctor for a proper prescription.")

def get_health_advice(symptom):
    advice = {
        "fever": "It sounds like you might have a fever. Stay hydrated and rest. If it persists, consult a doctor.",
        "headache": "Headaches can be caused by stress or dehydration. Try resting and drinking water.",
        "cough": "Persistent cough can be due to allergies or infection. Drink warm fluids and monitor symptoms.",
        "cold": "Common colds usually go away in a few days. Drink warm fluids and take rest.",
        "stomach pain": "Stomach pain may be due to indigestion or infection. Avoid spicy food and rest."
    }
    return advice.get(symptom.lower(), "I'm not sure about that. Please consult a medical professional.")

def chatbot_response(user_input):
    symptoms = ["fever", "headache", "cough", "cold", "stomach pain"]
    severity_levels = ["mild", "moderate", "severe"]
    
    for symptom in symptoms:
        if symptom in user_input.lower():
            severity = "mild"  # Default severity
            for level in severity_levels:
                if level in user_input.lower():
                    severity = level
                    break
            
            advice = get_health_advice(symptom)
            prescription = get_prescription(symptom, severity)
            return f"{advice}\nPrescription: {prescription}"
    
    return "I'm not sure how to respond to that. Please provide more details or consult a doctor."

# Main loop for chatbot interaction
print("AI Healthcare Chatbot: Hello! I am here to assist you with medical queries. Please describe your symptoms and severity (mild, moderate, or severe).")
while True:
    user_input = input("You: ")
    if user_input.lower() in ["exit", "quit", "bye"]:
        print("Chatbot: Take care! Stay healthy.")
        break
    response = chatbot_response(user_input)
    print("Chatbot:", response)
# GenAiAssignment
Ai Healthcare chatbot
