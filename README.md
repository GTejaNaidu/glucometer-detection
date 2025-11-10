# 🩸 Advanced Glucometer Detection System

A comprehensive web application for detecting and managing glucose readings using AI-powered OCR technology.

## 🌟 Features

- **AI-Powered OCR**: Uses Google Gemini API to extract glucose readings from images
- **Patient Management**: Complete patient records with medical history
- **Real-time Analytics**: Interactive charts and dashboards
- **Mobile & Desktop**: Fully responsive design for all devices
- **Camera Support**: Direct camera capture on mobile devices
- **Role-Based Access**: Doctor, Nurse, Admin, and Patient roles
- **Secure Authentication**: Password-protected with activity logging
- **Data Retention**: Automatic cleanup of inactive accounts

## 📱 Mobile Compatible

This application is fully optimized for mobile devices with:
- Responsive design
- Touch-friendly controls
- Camera integration
- Auto-collapsing sidebar
- Optimized layouts for all screen sizes

See [MOBILE_GUIDE.md](MOBILE_GUIDE.md) for detailed mobile usage instructions.

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- Google Gemini API Key ([Get one here](https://makersuite.google.com/app/apikey))

### Installation

1. Clone the repository:
```bash
git clone https://github.com/YOUR_USERNAME/glucometer-detection.git
cd glucometer-detection
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Run the application:
```bash
streamlit run b.py
```

4. Open your browser and navigate to `http://localhost:8501`

5. Enter your Google Gemini API key when prompted

## 🔑 API Key Setup

The application will prompt you to enter your Google Gemini API key on first launch. The key is stored securely in the session and not saved to disk.

To get your API key:
1. Visit [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Sign in with your Google account
3. Create a new API key
4. Copy and paste it into the application

## 📊 Usage

### For Healthcare Providers (Doctors/Nurses)

1. **Register/Login**: Create an account or login
2. **Add Patients**: Register new patients with complete medical information
3. **Upload Readings**: Take photos or upload glucometer images
4. **AI Detection**: Let AI extract glucose values automatically
5. **Track Progress**: View analytics and trends
6. **Manage Appointments**: Schedule and track patient appointments

### For Patients

1. **Self-Registration**: Create your own account
2. **Upload Readings**: Track your glucose levels
3. **View History**: See your reading trends
4. **Appointments**: View scheduled appointments
5. **Alerts**: Receive notifications for abnormal readings

## 🎨 Features Overview

### Dashboard
- Real-time statistics
- Recent readings
- Patient overview
- Quick actions

### Patient Management
- Comprehensive patient profiles
- Medical history tracking
- Emergency contacts
- Medication records

### Analytics
- Interactive charts
- Trend analysis
- Statistical insights
- Export capabilities

### Appointments
- Schedule management
- Reminders
- Status tracking

### Alerts
- Abnormal reading notifications
- System alerts
- Activity logs

## 🔒 Security Features

- Password hashing with SHA-256
- Session-based authentication
- Activity logging
- Account lockout after failed attempts
- Role-based access control
- Secure API key handling

## 📱 Mobile Access

### Local Network
```bash
# Find your IP address
ipconfig  # Windows
ifconfig  # Mac/Linux

# Access from mobile
http://YOUR_IP_ADDRESS:8501
```

### Cloud Deployment
Deploy to Streamlit Cloud for public access (see deployment section below)

## 🚀 Deployment

### Streamlit Cloud (Recommended)

1. Push your code to GitHub
2. Visit [share.streamlit.io](https://share.streamlit.io)
3. Sign in with GitHub
4. Click "New app"
5. Select your repository
6. Set main file: `b.py`
7. Deploy!

### Other Platforms

- **Heroku**: Use `Procfile` and `setup.sh`
- **AWS/Azure/GCP**: Use containerization with Docker
- **Railway**: Direct GitHub integration

## 📁 Project Structure

```
OCR/
├── b.py                          # Main application file
├── requirements.txt              # Python dependencies
├── README.md                     # This file
├── MOBILE_GUIDE.md              # Mobile usage guide
├── MOBILE_CHANGES.md            # Technical changes
├── imge.png                     # Logo image
├── glucometer_app.db            # SQLite database (auto-created)
└── .gitignore                   # Git ignore rules
```

## 🛠️ Technology Stack

- **Frontend**: Streamlit
- **AI/ML**: Google Gemini API
- **Database**: SQLite
- **Charts**: Plotly
- **Image Processing**: Pillow
- **Data Analysis**: Pandas

## 📖 Documentation

- [Mobile Guide](MOBILE_GUIDE.md) - Complete mobile usage instructions
- [Mobile Changes](MOBILE_CHANGES.md) - Technical implementation details
- [Role-Based Access Control](ROLE_BASED_ACCESS_CONTROL.md) - Security features
- [Data Retention Policy](DATA_RETENTION_POLICY.md) - Data management

## 🐛 Troubleshooting

### Camera not working?
- Ensure HTTPS connection (required for camera access)
- Check browser permissions
- Try different browser

### API errors?
- Verify API key is correct
- Check internet connection
- Ensure API quota is not exceeded

### Database locked?
- Close other instances of the app
- Check file permissions
- Restart the application

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License.

## 👨‍💻 Author

Created with ❤️ for better healthcare management

## 🙏 Acknowledgments

- Google Gemini API for AI capabilities
- Streamlit for the amazing framework
- All contributors and users

## 📞 Support

For issues or questions:
1. Check the documentation
2. Search existing issues
3. Create a new issue with details

---

**Version**: 2.0  
**Last Updated**: November 2025  
**Status**: Production Ready ✅
