# NgA
Search Engine 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NexusTech | Futuristic Sales Experience</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/three@0.132.2/build/three.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/gsap@3.12.2/dist/gsap.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/tsparticles@2.12.0/tsparticles.min.js"></script>
    <style>
        :root {
            --primary: #6c5ce7;
            --secondary: #00cec9;
            --accent: #fd79a8;
            --dark: #2d3436;
            --light: #dfe6e9;
            --glass: rgba(255, 255, 255, 0.1);
            --glass-border: rgba(255, 255, 255, 0.2);
            --transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
            color: var(--light);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        #particles-js {
            position: absolute;
            width: 100%;
            height: 100%;
            z-index: -1;
        }

        .glass-card {
            background: var(--glass);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid var(--glass-border);
            border-radius: 20px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
            overflow: hidden;
            transition: var(--transition);
        }

        .glass-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 35px rgba(108, 92, 231, 0.3);
        }

        header {
            padding: 1.5rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: relative;
            z-index: 10;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.8rem;
            font-weight: 700;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .logo i {
            font-size: 2.2rem;
        }

        nav ul {
            display: flex;
            gap: 2rem;
            list-style: none;
        }

        nav a {
            color: var(--light);
            text-decoration: none;
            font-weight: 500;
            position: relative;
            padding: 0.5rem 0;
        }

        nav a:after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            transition: var(--transition);
        }

        nav a:hover:after {
            width: 100%;
        }

        .hero {
            padding: 5rem 5% 8rem;
            text-align: center;
            position: relative;
            z-index: 5;
        }

        .hero h1 {
            font-size: 4rem;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 1.5rem;
            line-height: 1.2;
        }

        .hero p {
            font-size: 1.5rem;
            max-width: 800px;
            margin: 0 auto 2.5rem;
            opacity: 0.9;
        }

        .cta-button {
            display: inline-block;
            padding: 1rem 2.5rem;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            color: white;
            border-radius: 50px;
            font-weight: 600;
            text-decoration: none;
            font-size: 1.2rem;
            transition: var(--transition);
            border: none;
            cursor: pointer;
            box-shadow: 0 10px 20px rgba(108, 92, 231, 0.3);
        }

        .cta-button:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(108, 92, 231, 0.4);
        }

        .features {
            padding: 0 5% 8rem;
            position: relative;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 5rem;
            position: relative;
        }

        .section-title:after {
            content: '';
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 4px;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            border-radius: 2px;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2.5rem;
        }

        .feature-card {
            padding: 2.5rem;
            text-align: center;
        }

        .feature-icon {
            font-size: 3.5rem;
            margin-bottom: 1.5rem;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .feature-card h3 {
            font-size: 1.8rem;
            margin-bottom: 1rem;
        }

        .feature-card p {
            opacity: 0.8;
            line-height: 1.6;
        }

        .products {
            padding: 0 5% 8rem;
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2.5rem;
        }

        .product-card {
            padding: 2rem;
            position: relative;
            overflow: hidden;
        }

        .product-badge {
            position: absolute;
            top: 20px;
            right: 20px;
            padding: 0.5rem 1rem;
            background: linear-gradient(90deg, var(--accent), #e84393);
            border-radius: 30px;
            font-size: 0.9rem;
            font-weight: 600;
        }

        .product-image {
            width: 100%;
            height: 200px;
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 1.5rem;
            position: relative;
        }

        #product-canvas {
            width: 100%;
            height: 100%;
        }

        .product-info {
            text-align: center;
        }

        .product-info h3 {
            font-size: 1.5rem;
            margin-bottom: 0.5rem;
        }

        .product-price {
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 1.5rem;
            color: var(--secondary);
        }

        .product-actions {
            display: flex;
            justify-content: center;
            gap: 1rem;
        }

        .action-button {
            padding: 0.7rem 1.5rem;
            border-radius: 30px;
