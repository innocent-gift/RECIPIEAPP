Recipe Generator App
A Dockerized Web Application with Load Balancing

This project is a Recipe Generator that fetches recipes from an external API (The MealDB) and displays them in a user-friendly web interface. It is containerized using Docker, deployed on two web servers (web-01 & web-02), and load-balanced using haproxy on lb-01.

📌 Features
✅ Fetches recipes from The MealDB API
✅ Search functionality to find recipes by name
✅ Responsive UI built with HTML, CSS, and JavaScript
✅ Dockerized for easy deployment
✅ Load-balanced across two backend servers

🚀 Deployment Architecture
text
User → [HAProxy Load Balancer (lb-01)] → [Web-01 (Docker Container)]  
                               ↘→ [Web-02 (Docker Container)]
📦 Docker Hub Image
🔗 Repository: https://hub.docker.com/r/innocent2/recipe-generator
📌 Tags: v1, latest

🔧 Setup & Deployment
1️⃣ Build the Docker Image Locally
sh
docker build -t innocent2/recipe-generator:v1 .
2️⃣ Test Locally
sh
docker run -p 8080:8080 innocent2/recipe-generator:v1
Verify:

sh
curl http://localhost:8080
# or open in browser: http://localhost:8080
3️⃣ Push to Docker Hub
sh
docker login
docker push innocent2/recipe-generator:v1
🖥️ Deploy on Web Servers (web-01 & web-02)
SSH into each server and run:
sh
docker pull innocent2/recipe-generator:v1
docker run -d --name app --restart unless-stopped -p 8080:8080 innocent2/recipe-generator:v1
Verify:

sh
curl http://web-01:8080  # Should return the app
curl http://web-02:8080  # Should return the app
⚖️ Configure Load Balancer (lb-01)
Update HAProxy Config (/etc/haproxy/haproxy.cfg)
sh
backend webapps
    balance roundrobin
    server web01 172.20.0.11:8080 check
    server web02 172.20.0.12:8080 check
Reload HAProxy
sh
docker exec -it lb-01 sh -c 'haproxy -sf $(pidof haproxy) -f /etc/haproxy/haproxy.cfg'
✅ Testing Load Balancing
Run multiple requests to see traffic distributed:

sh
curl http://localhost  # (or the exposed lb-01 port)
Expected Result: Responses alternate between web-01 and web-02.

🔒 Security Note (Optional Bonus)
To avoid hardcoding API keys in the Docker image:

Use environment variables:

sh
docker run -d -e API_KEY=your_key --name app -p 8080:8080 innocent2/recipe-generator:v1
Or use Docker Secrets / Kubernetes ConfigMaps in production.

📜 API Reference
🔗 The MealDB API Documentation

📹 Demo Video
🎥 Watch the Demo (Not exceeding 2 minutes)

📝 Final Notes
No API keys are exposed in the repository (handled via .gitignore).

Tested on Docker with HAProxy for seamless load balancing.

Future improvements: Caching, user authentication, and more recipe filters.

🌟 Happy Cooking! 🍳🚀

Developed by Nkurunziza Innocent
🔗 GitHub: https://github.com/innocent-gift
📧 Email: i.nkurunziza@alustudent.com

This README.md is clear, structured, and reproducible, ensuring smooth grading. 🚀 Let me know if you'd like any refinements!
