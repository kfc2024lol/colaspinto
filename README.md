<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Colaspinto</title>
    <style>
        body {
            margin: 0;
            font-family: sans-serif;
        }

        .header {
            background-color: #111;
            color: #fff;
            padding: 1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: fixed; /* Mantiene la barra de navegación en la parte superior */
            width: 100%; /* Asegura que la barra de navegación ocupe todo el ancho */
            z-index: 10; /* Asegura que esté por encima del banner */
        }

        .logo {
            width: 50px;
        }

        .nav {
            display: flex;
            list-style: none;
            margin: 0;
            padding: 0;
        }

            .nav li {
                margin-right: 1rem;
                position: relative; /* Necesario para el submenú */
            }

            .nav a {
                color: #fff;
                text-decoration: none;
            }

        /* Estilos para el submenú */
        .sub-menu {
            display: none; /* Oculta el submenú por defecto */
            position: absolute; /* Posiciona el submenú relativo al elemento padre */
            background-color: #222; /* Color de fondo del submenú */
            padding: 0.5rem; /* Espaciado interno */
            z-index: 20; /* Asegura que el submenú esté por encima de otros elementos */
        }

        .nav li:hover .sub-menu {
            display: block; /* Muestra el submenú al pasar el cursor */
        }

        .hero {
            background-image: url("bannerutp.jpg");
            background-size: cover;
            background-position: center;
            min-height: 800px;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            overflow: hidden;
            padding-top: 00px; /* Aumenta este valor para evitar que el banner se esconda */
        }

            .hero::before {
                content: "";
                position: absolute;
                top: 0;
                left: 0;
                right: 0;
                bottom: 0;
                z-index: 1;
            }

        .hero-text {
            text-align: center;
            color: #fff;
            font-size: 3rem;
            position: relative; /* Asegura que el texto esté por encima del fondo oscuro */
            z-index: 2; /* Asegura que el texto esté por encima del fondo oscuro */
        }

        .footer {
            background-color: #111;
            color: #fff;
            padding: 1rem;
            text-align: center;
        }

        .carousel {
            display: flex;
            overflow: hidden;
            position: relative;
            width: 100%; /* Asegura que el carrusel ocupe todo el ancho */
        }

        .carousel-container {
            display: flex;
            transition: transform 0.5s ease;
        }

        .carousel video {
            max-width: 100%; /* Asegura que los videos no excedan el ancho del contenedor */
            height: auto; /* Mantiene la proporción del video */
            flex: 0 0 100%; /* Cada video ocupa el 100% del ancho del contenedor */
        }

        .nav-buttons {
            margin-top: 1rem;
            text-align: center;
        }

            .nav-buttons button {
                margin: 0 0.5rem;
                padding: 0.5rem 1rem;
                background-color: #111;
                color: #fff;
                border: none;
                cursor: pointer;
            }

                .nav-buttons button:hover {
                    background-color: #333; /* Cambia el color al pasar el mouse */
                }
    </style>
</head>
<body>
    <header class="header">
        <img src="logo1.png" alt="Lamborghini Logo" class="logo">
        <nav>
            <ul class="nav">
                <li><a href="#Novedades">Novedades </a></li>
                <li>
                    <a href="#contact">Contactos</a>
                    <div class="sub-menu">
                        <a href="https://www.youtube.com" target="_blank">YouTube</a>
                        <a href="https://www.instagram.com" target="_blank">Instagram</a>
                        <a href="https://www.twitter.com" target="_blank">Twitter</a>
                    </div>
                </li>
            </ul>
        </nav>
    </header>
    <section class="hero">
        <div class="hero-text">
        </div>
    </section>
    <footer class="footer">
        <p>&copy; (Rivero, Peralta, Merlo, Bustos, García) </p>
    </footer>
    <div class="carousel" id="carousel">
        <div class="carousel-container" id="carouselContainer">
            <video muted autoplay loop>
                <source src="video.mp4" type="video/mp4">
            </video>
            <video muted autoplay loop>
                <source src="patatus.mp4" type="video/mp4">
            </video>
            <video muted autoplay loop>
                <source src="rebeca.mp4" type="video/mp4">
            </video>
        </div>
    </div>
    <div class="nav-buttons">
        <button onclick="prevVideo()">Ant</button>
        <button onclick="nextVideo()">Sig</button>
    </div>
    <script>
        window.addEventListener('scroll', function () {
            const banner = document.querySelector('.hero');
            const scrollPosition = window.scrollY;
            const opacity = 1 - Math.min(scrollPosition / 300, 1); // Cambia la opacidad según el desplazamiento
            const translateY = Math.min(scrollPosition, 100); // Desplazamiento hacia arriba
            banner.style.opacity = opacity; // Ajusta la opacidad del banner
            banner.style.transform = `translateY(-${translateY}px)`; // Mueve el banner hacia arriba
        });

        let currentIndex = 0;
        const videos = document.querySelectorAll('.carousel video');
        const totalVideos = videos.length;

        function updateCarousel() {
            const carouselContainer = document.getElementById('carouselContainer');
            const offset = -currentIndex * 100; // Cada video ocupa el 100% del ancho del contenedor
            carouselContainer.style.transform = `translateX(${offset}%)`;
        }

        function nextVideo() {
            currentIndex = (currentIndex + 1) % totalVideos;
            updateCarousel();
        }

        function prevVideo() {
            currentIndex = (currentIndex - 1 + totalVideos) % totalVideos;
            updateCarousel();
        }
    </script>
</body>
</html>
