 Recipe Generator Web Application

 Table of Contents

 1. OVERVIEW

The Recipe Generator is a web application that helps users discover and explore recipes from around the world. The application provides an intuitive interface to search, filter, and browse recipes from The Spoonacular API, complete with detailed instructions, ingredients, and meal categories.

Note: This application is intended for educational purposes and recipe inspiration. Always verify food allergies and dietary requirements before preparing any recipes.

 2. FEATURES

 2.1 Comprehensive Recipe Database
Access to hundreds of recipes with detailed information
Categorised by meal type, cuisine, and main ingredients
  recipe data from The Spoonacular API

 2.2 Advanced Search and Filtering
Search functionality by recipe name
 Filter by category (vegetarian, vegan, desserts, etc.)
 Dynamic search results with instant updates

2.3 Interactive Recipe Cards
Detailed recipe information display
 Expandable modal views for complete recipe details
 Ingredient lists with measurements

2.4 User Experience Features
Responsive design for all devices
Clean, intuitive interface
 Loading states and error handling
 Accessibility-focused design

 3. DEMO


3.1 YOUTUBE LINK
YouTube link: https://www.youtube.com/watch?v=CoIItWS_EgQ

3.2 GITHUB LINK
Live application URL: https://innocent-gift.github.io/RECIPIEAPP/

 4. TECHNOLOGIES USED

Frontend: HTML5, CSS3, JavaScript
API Integration: The Spoonacular API
Containerization: Docker
Load Balancing: HAProxy
Deployment: Nginx web servers

5. API INTEGRATION

The application integrates with the Spoonacular API to access a comprehensive database of recipes. This API provides:
Complete recipe information, including names, categories, and regions
Detailed ingredient lists and measurements
Step-by-step cooking instructions
Thumbnail images for each recipe

API Documentation: [The Spoonacular API Documentation](https://www.theSpoonacular.com/api.php)

6. LOCAL DEVELOPMENT SETUP

Follow these steps to set up the project locally:

Type this code: 
```
git clone https://github.com/innocent-gift/RECIPIEAPP.git
```
then move in the directory called RECIPIEAPP
```
cd RECIPIEAPP 
```
then open index.html in the browser
7. DEPLOYMENT

7.1 Prerequisites
- Two web servers (web-01 and web-02) with Docker installed
- Load balancer (lb-01) with HAProxy installed

 7.2 Docker Deployment

Docker Hub Images:
Web Servers: `docker pull innocent2/RECIEPIEAPP:v1`
 Load Balancer: Custom HAProxy configuration

 From the image below, you can see that all servers are running and the load balancer is balancing the servers well check it there in tesing them.

Testing:
Verify load balancing by running:
```bash
curl http://localhost
```
<img width="2230" height="545" alt="Screenshot 2025-07-31 200055" src="https://github.com/user-attachments/assets/14f732a2-6696-42c1-abd2-35d996b7372c" />


Responses should alternate between

 8. CHALLENGES AND SOLUTIONS

API Rate Limiting: The free tier of The Spoonacular API has limitations. Implemented client-side caching to reduce API calls.

Security: Avoided hardcoding API keys by using environment variables:
```bash
docker run -d -e API_KEY=your_key --name app -p 8080:8080 innocent2/recipe-generator:v1
```

 9. CREDITS AND ACKNOWLEDGMENTS

API Used: The Spoonacular API
Infrastructure: ALX Africa program
Docker Community for excellent documentation






Developed by Nkurunziza Innocent  
🔗 GitHub: [https://github.com/innocent-gift](https://github.com/innocent-gift)  
📧 Email: i.nkurunziza@alustudent.com  
🌐 Portfolio: [https://innocent-gift.github.io](https://innocent-gift.github.io)

