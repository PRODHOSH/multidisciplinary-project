# Smart Soil Moisture Monitoring and Irrigation Recommendation System

## 📋 Project Overview

The **Smart Soil Moisture Monitoring and Irrigation Recommendation System** is a multidisciplinary project that combines hardware sensors, web technologies, and artificial intelligence to help farmers optimize their irrigation practices. By monitoring real-time soil conditions and leveraging machine learning algorithms, the system provides intelligent water recommendations, reducing water waste and improving crop yield.

This project bridges the gap between IoT hardware and intelligent software systems, creating a practical solution for sustainable agriculture.

---

## 🌾 Problem Statement

Traditional irrigation methods often lead to:
- **Over-watering or under-watering** of crops due to lack of real-time soil data
- **Water wastage**, contributing to resource depletion
- **Reduced crop productivity** caused by improper moisture levels
- **Manual monitoring**, which is time-consuming and inefficient

Farmers need an automated, data-driven solution that provides actionable insights for efficient water management.

---

## 🎯 Objectives

1. Develop a **hardware system** using soil moisture sensors, Arduino, and a water pump to monitor and control irrigation
2. Build a **web-based dashboard** for real-time visualization of soil conditions
3. Integrate **AI/ML models** to predict optimal water requirements based on environmental factors
4. Provide an **interactive simulation mode** for testing and demonstration purposes
5. Create a scalable system that can be deployed for small-scale and large-scale farming

---

## ✨ Features

### Current Implementation (Review-II Stage)

- **Real-time Data Visualization**: Display soil moisture, temperature, and humidity on an interactive dashboard
- **AI-Powered Recommendations**: Machine learning model predicts water requirements based on:
  - Soil type (clay, loam, sandy)
  - Current moisture levels
  - Temperature and humidity
  - Historical data patterns
- **Simulation Mode**: Interactive sliders allow users to simulate different soil conditions and view system responses
- **Crop Selection**: Choose specific crops to get tailored irrigation recommendations
- **Graphical Analytics**: Visual charts showing moisture levels vs. irrigation suggestions over time
- **Weather Integration**: Fetch real-time environmental data using OpenWeather API
- **Responsive UI**: Mobile-friendly web interface for accessibility

### Hardware Components

- Soil moisture sensor for accurate ground-level readings
- Arduino microcontroller for data processing
- Water pump for automated irrigation control
- (Future) Serial/API communication with software dashboard

---

## 🏗️ System Architecture

### Hardware Layer
```
Soil Moisture Sensor → Arduino Microcontroller → Water Pump
                           ↓
                    Serial/API Communication
                           ↓
                    Backend Server
```

### Software Layer
```
Frontend (HTML/CSS/JS) ↔ Flask Backend ↔ ML Model
                              ↓
                        OpenWeather API
                              ↓
                        Database (Future)
```

### Data Flow
1. **Sensor reads** soil moisture, temperature, and humidity
2. **Arduino processes** the sensor data
3. **Data transmitted** to Flask backend (currently simulated)
4. **ML model analyzes** environmental conditions and historical patterns
5. **Dashboard displays** real-time data and recommendations
6. **User receives** actionable irrigation advice
7. **Optional**: Automated pump activation based on threshold values

---

## 🛠️ Tech Stack

### Frontend
- HTML5, CSS3, JavaScript
- Chart.js / Plotly for data visualization
- Bootstrap (optional) for responsive design

### Backend
- **Python 3.x**
- **Flask** - Web framework for API and routing
- Alternative: Streamlit for rapid prototyping

### Machine Learning
- **Scikit-learn** - For building predictive models
- Pandas & NumPy - Data manipulation and processing
- Rule-based algorithms for baseline predictions

### Hardware
- Arduino Uno/Nano
- Capacitive/Resistive Soil Moisture Sensor
- DHT11/DHT22 Temperature & Humidity Sensor
- Relay module and water pump

### APIs & Integration
- **OpenWeather API** - Real-time weather data
- Serial communication (PySerial) for Arduino integration
- RESTful APIs for future cloud deployment

### Future Enhancements
- Firebase/AWS for cloud hosting
- MySQL/PostgreSQL for historical data storage
- MQTT protocol for IoT communication

---

## ⚙️ How It Works

### Step-by-Step Workflow

1. **Data Collection**
   - Soil moisture sensor measures volumetric water content in the soil
   - Temperature and humidity sensors capture environmental conditions
   - (Current stage: Simulated data via web interface sliders)

2. **Data Transmission**
   - Arduino collects sensor readings at regular intervals
   - Data is transmitted to the Flask backend via serial communication or API
   - (Current stage: Manual input or random generation for demonstration)

3. **Environmental Context**
   - System fetches current weather conditions from OpenWeather API
   - Includes precipitation forecast, temperature, and humidity

4. **AI/ML Analysis**
   - Input features: soil moisture %, temperature, humidity, soil type, crop type
   - ML model (trained on agricultural datasets) predicts:
     - Optimal moisture level for selected crop
     - Recommended water volume
     - Irrigation timing
   - Rule-based fallback for edge cases

5. **Recommendation Generation**
```python
   if current_moisture < optimal_moisture:
       recommendation = "Irrigate now"
       water_amount = calculate_deficit(optimal - current)
   elif current_moisture > optimal_moisture:
       recommendation = "No irrigation needed"
   else:
       recommendation = "Optimal moisture level"
```

6. **Visualization & User Interaction**
   - Dashboard displays real-time metrics with color-coded indicators
   - Graphs show moisture trends over time
   - Interactive simulation mode for testing different scenarios

7. **Automated Control (Future)**
   - System triggers water pump based on recommendations
   - Feedback loop updates soil moisture readings
   - Historical data stored for model improvement

---

## 📊 Screenshots

*Screenshots will be added here showcasing:*

1. **Dashboard Home Page** - Overview of current soil conditions
2. **Recommendation Panel** - AI-powered irrigation suggestions
3. **Simulation Mode** - Interactive sliders for testing
4. **Analytics Page** - Historical moisture and irrigation trends
5. **Hardware Setup** - Arduino with sensors and pump

---

## 🚀 Installation & Setup

### Prerequisites
- Python 3.8 or higher
- pip package manager
- Arduino IDE (for hardware integration)
- OpenWeather API key (free tier available)

### Software Setup

1. Clone the repository
```bash
git clone https://github.com/yourusername/smart-irrigation-system.git
cd smart-irrigation-system
```

2. Install dependencies
```bash
pip install -r requirements.txt
```

3. Configure API keys
```bash
# Create a .env file
echo "OPENWEATHER_API_KEY=your_api_key_here" > .env
```

4. Run the Flask application
```bash
python app.py
```

5. Access the dashboard
```
Open browser and navigate to: http://localhost:5000
```

### Hardware Setup (Optional)

1. Connect soil moisture sensor to Arduino analog pin A0
2. Connect DHT11 sensor to digital pin D2
3. Connect relay module to digital pin D7 (for pump control)
4. Upload Arduino sketch from `/hardware/arduino_code.ino`
5. Connect Arduino to computer via USB

---

## 📂 Project Structure
```
smart-irrigation-system/
│
├── app.py                      # Main Flask application
├── requirements.txt            # Python dependencies
├── README.md                   # Project documentation
│
├── templates/                  # HTML templates
│   ├── index.html             # Dashboard home page
│   ├── simulation.html        # Simulation mode interface
│   └── analytics.html         # Data visualization page
│
├── static/                     # Static assets
│   ├── css/
│   │   └── style.css          # Custom styles
│   ├── js/
│   │   └── charts.js          # Chart rendering logic
│   └── images/
│
├── models/                     # Machine learning models
│   ├── irrigation_model.pkl   # Trained ML model
│   └── train_model.py         # Model training script
│
├── hardware/                   # Arduino code
│   └── arduino_code.ino       # Sensor reading sketch
│
└── utils/                      # Helper functions
    ├── api_handler.py         # OpenWeather API integration
    └── predictor.py           # ML prediction logic
```

---

## 🔮 Future Scope

### Phase 1: Hardware-Software Integration
- Real-time data streaming from Arduino to web dashboard
- Automated pump control based on ML recommendations
- SMS/Email alerts for critical moisture levels

### Phase 2: Cloud Deployment
- Deploy dashboard on AWS/Firebase for remote access
- Mobile application for Android/iOS
- Multi-user support for farm management teams

### Phase 3: Advanced Analytics
- Predictive analytics for seasonal irrigation planning
- Soil health monitoring with additional sensors (pH, NPK)
- Integration with satellite imagery for large-scale farming

### Phase 4: Scalability & Intelligence
- Support for multiple sensor nodes across different field zones
- Deep learning models for crop disease prediction
- Integration with drip irrigation and smart sprinkler systems
- Blockchain-based data logging for agricultural compliance

---

## 👥 Team Members

### Hardware Development Team
1. **[Member Name 1]** - Hardware Design & Arduino Programming
2. **[Member Name 2]** - Sensor Integration & Testing

### Software Development Team
3. **[Member Name 3]** - Frontend Development & UI/UX
4. **[Member Name 4]** - Backend Development & API Integration
5. **[Member Name 5]** - AI/ML Model Development & Data Analysis

---

## 🤝 Contributing

We welcome contributions to improve this project! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is developed for educational purposes as part of the Basic Multidisciplinary Project course.

---

## 🙏 Acknowledgments

This project was developed as part of the **Basic Multidisciplinary Project (BACSE191)** under **VIT CHENNAI**, demonstrating the integration of hardware, software, and AI for sustainable agriculture. 

We express our gratitude to:
- Our project guide and faculty mentors for their continuous support
- VIT Chennai for providing resources and infrastructure
- The open-source community for valuable tools and libraries
- Agricultural experts who provided domain insights

---

## 📞 Contact

For queries or collaboration opportunities, please reach out to:
- **Email**: [team.email@example.com]
- **Project Repository**: [GitHub Link]

---

**Built with ❤️ for Sustainable Agriculture**
