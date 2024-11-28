<!DOCTYPE html>
 <html>
 <head>
    <title>Interactive Gallery</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background-color: beige;
            overflow: hidden;
        }


        #welcome-text {
            font-size: 5em;
            font-family: 'RusticRoadway', cursive;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 2;
            text-align: center;
            width: 50%;
            justify-content: center;
            animation: fadeIn 1.5s;
            font-weight: bold;
        }


        #instructions {
            position: absolute;
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background-color: beige;
            z-index: 2;
            font-family: cursive;
            animation: fadeIn 1s;
        }


        #startButton {
            padding: 15px 30px;
            font-size: 20px;
            margin-top: 20px;
            cursor: crosshair;
            font-family: cursive;
            animation: fadeIn 1s;
            transition: 0.4s ease;
        }


        #startButton:hover {
            background: #ffc773;
            box-shadow: 0 0 5px #ffc773,
                        0 0 20px #ffc773,
                        0 0 60px #ffc773,
                        0 0 150px #ffc773;
        }


        #gallery {
            display: none;
            width: 100vw;
            height: 100vh;
            position: relative;
        }


        .gallery-row {
            display: flex;
            justify-content: space-between;
            width: 100%;
            padding: 20px 5%;
            box-sizing: border-box;
            position: absolute;
        }


        .gallery-row:first-child {
            top: 0;
        }


        .gallery-row:last-child {
            bottom: 0;
        }


        .gallery-image {
            width: 9%;
            height: auto;
            aspect-ratio: 1;
            border: 2px solid black;
            object-fit: cover;
        }


        #character {
            width: 100px;
            height: 100px;
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            z-index: 1;
        }


        #fullscreen-view {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.9);
            z-index: 3;
        }


        #fullscreen-image {
            max-width: 90%;
            max-height: 90%;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
        #gallery-name {
           position: fixed;
           top: 50%;
           left: 50%;
           transform: translate(-50%, -50%);
           font-size: 4em;
           color: black;
           transition: opacity 0.7s;
           z-index: 5;
           display: none;
           text-align: center;
           font-family: 'RusticRoadway', cursive;
           font-weight: bold;
           pointer-events: none;
           background-color: rgba(245, 245, 220, 0.8);
        }
        @keyframes fadeIn {
            0% {
                opacity: 0;
            }
            100% {
                opacity: 1;
            }
        }
        @keyframes fadeOut {
            0% {
                opacity: 1;
            }
            100% {
                opacity: 0;
            }
        }
        @font-face {
            font-family: 'RusticRoadway';
            src: url('C:/Users/Admin/Downloads/RusticRoadway.woff') format('woff');
        }


    </style>
 </head>
 <body>
    <div id="welcome-text">Welcome to <br> Oxford 22-25's <br> Photo Gallery</div>
    <div id="instructions">
        <h1>Instructions</h1>
        <p>Use arrow keys to move the character around</p>
        <p>Press SPACE when near an image to view it in full screen</p>
        <p>Press ESC to exit full screen view</p>
        <p>Move to screen edges to navigate between galleries</p>
        <button id="startButton">Enter Gallery</button>
    </div>


    <div id="gallery">
        <img id="character" src="https://drive.google.com/uc?export=view&id=1Iaww-GryMpqu-swUXvKd767JCGHeS2tl" alt="Moving Character">
        <div class="gallery-row">
            <img class="gallery-image" src="H:\Nguyen Duy Hung\Bòfỏd\10\IMG_0057.JPG" alt="Gallery Image">
            <img class="gallery-image" src="H:\Nguyen Duy Hung\Bòfỏd\10\IMG_0071.JPG" alt="Gallery Image">
            <img class="gallery-image" src="H:\Nguyen Duy Hung\Bòfỏd\10\IMG_0090.JPG" alt="Gallery Image">
            <img class="gallery-image" src="H:\Nguyen Duy Hung\Bòfỏd\10\IMG20220912124126.jpg" alt="Gallery Image">
            <img class="gallery-image" src="H:\Nguyen Duy Hung\Bòfỏd\10\IMG20220924141748.jpg" alt="Gallery Image">
            <img class="gallery-image" src="H:\Nguyen Duy Hung\Bòfỏd\10\IMG20221020114222.jpg" alt="Gallery Image">
        </div>
        <div class="gallery-row">
            <img class="gallery-image" src="gallery1_7.jpg" alt="Gallery Image">
            <img class="gallery-image" src="gallery1_8.jpg" alt="Gallery Image">
            <img class="gallery-image" src="gallery1_9.jpg" alt="Gallery Image">
            <img class="gallery-image" src="gallery1_10.jpg" alt="Gallery Image">
            <img class="gallery-image" src="gallery1_11.jpg" alt="Gallery Image">
            <img class="gallery-image" src="gallery1_12.jpg" alt="Gallery Image">
        </div>
    </div>


    <div id="fullscreen-view">
        <img id="fullscreen-image" src="" alt="Fullscreen Image">
    </div>


    <div id="gallery-name"></div>


    <script>
        // Add this right after your <body> tag's script section starts
        document.addEventListener('DOMContentLoaded', () => {
            const welcomeText = document.getElementById('welcome-text');
            const instructions = document.getElementById('instructions');
           
            // Initially hide instructions
            instructions.style.display = 'none';
            welcomeText.style.opacity = '1'; // Ensure welcome text starts fully visible
           
            // After 2 seconds, fade out welcome text and show instructions
            setTimeout(() => {
                welcomeText.style.animation = 'fadeOut 1s forwards'; // Add 'forwards' to maintain final state
            }, 2000);
            setTimeout(() => {
                welcomeText.style.display = 'none';
                instructions.style.display = 'flex';
                instructions.style.animation = 'fadeIn 1s';
            }, 3000);
        });
        let currentGallery = 0;
        const totalGalleries = 5;
        const character = {
            x: window.innerWidth / 2,
            y: window.innerHeight / 2,
            speed: 8
        };
        // Add this with your other constants
        const galleryNames = {
            0: "Grade 10 - 2022",
            1: "Grade 11 - 2023",
            2: "Grade 12 - 2024",
            3: "Ocean Gallery",
            4: "City Gallery"
        };


        const galleryImages = {
            0: {
                top: ['H:/Nguyen Duy Hung/Bòfỏd/10/IMG_0057.JPG',
                      'H:/Nguyen Duy Hung/Bòfỏd/10/IMG_0071.JPG',
                      'H:/Nguyen Duy Hung/Bòfỏd/10/IMG_0090.JPG',
                      'H:/Nguyen Duy Hung/Bòfỏd/10/IMG20220912124126.jpg',
                      'H:/Nguyen Duy Hung/Bòfỏd/10/IMG20220924141748.jpg',
                      'H:/Nguyen Duy Hung/Bòfỏd/10/IMG20221020114222.jpg'  
                ],
                bottom: ['gallery1_7.jpg', 'gallery1_8.jpg', 'gallery1_9.jpg', 'gallery1_10.jpg', 'gallery1_11.jpg', 'gallery1_12.jpg']
            },
            1: {
                top: ['H:/Nguyen Duy Hung/Bòfỏd/10/received_523757756501881.jpeg', 'gallery2_2.jpg', 'gallery2_3.jpg', 'gallery2_4.jpg', 'gallery2_5.jpg', 'gallery2_6.jpg'],
                bottom: ['gallery2_7.jpg', 'gallery2_8.jpg', 'gallery2_9.jpg', 'gallery2_10.jpg', 'gallery2_11.jpg', 'gallery2_12.jpg']
            },
            2: {
                top: ['gallery3_1.jpg', 'gallery3_2.jpg', 'gallery3_3.jpg', 'gallery3_4.jpg', 'gallery3_5.jpg', 'gallery3_6.jpg'],
                bottom: ['gallery3_7.jpg', 'gallery3_8.jpg', 'gallery3_9.jpg', 'gallery3_10.jpg', 'gallery3_11.jpg', 'gallery3_12.jpg']
            },
            3: {
                top: ['gallery4_1.jpg', 'gallery4_2.jpg', 'gallery4_3.jpg', 'gallery4_4.jpg', 'gallery4_5.jpg', 'gallery4_6.jpg'],
                bottom: ['gallery4_7.jpg', 'gallery4_8.jpg', 'gallery4_9.jpg', 'gallery4_10.jpg', 'gallery4_11.jpg', 'gallery4_12.jpg']
            },
            4: {
                top: ['gallery5_1.jpg', 'gallery5_2.jpg', 'gallery5_3.jpg', 'gallery5_4.jpg', 'gallery5_5.jpg', 'gallery5_6.jpg'],
                bottom: ['gallery5_7.jpg', 'gallery5_8.jpg', 'gallery5_9.jpg', 'gallery5_10.jpg', 'gallery5_11.jpg', 'gallery5_12.jpg']
            }
        };


        document.getElementById('startButton').addEventListener('click', () => {
            document.getElementById('instructions').style.display = 'none';
            document.getElementById('gallery').style.display = 'block';
            loadGallery(currentGallery);
           
            // Show initial gallery name
            const galleryNameElement = document.getElementById('gallery-name');
            galleryNameElement.textContent = galleryNames[currentGallery];
            galleryNameElement.style.display = 'block';
            galleryNameElement.style.visibility = 'visible';
            galleryNameElement.style.animation = 'fadeIn 0.7s';
           
            // Fade out after 2 seconds
            setTimeout(() => {
                galleryNameElement.style.display = 'none';
                setTimeout(() => {
                galleryNameElement.style.display = 'none';
                galleryNameElement.style.visibility = 'hidden';
            }, 700);
            }, 3000);
        });


        document.addEventListener('keydown', (e) => {
            const char = document.getElementById('character');
           
            switch(e.key) {
                case 'ArrowLeft':
                    character.x = Math.max(0, character.x - character.speed);
                    if(character.x <= 0) switchGallery('prev');
                    break;
                case 'ArrowRight':
                    character.x = Math.min(window.innerWidth - 100, character.x + character.speed);
                    if(character.x >= window.innerWidth - 100) switchGallery('next');
                    break;
                case 'ArrowUp':
                    character.y = Math.max(0, character.y - character.speed);
                    break;
                case 'ArrowDown':
                    character.y = Math.min(window.innerHeight - 100, character.y + character.speed);
                    break;
                case ' ':
                    checkImageCollision();
                    break;
                case 'Escape':
                    document.getElementById('fullscreen-view').style.display = 'none';
                    break;
            }
           
            char.style.left = character.x + 'px';
            char.style.top = character.y + 'px';
        });


        function loadGallery(galleryIndex) {
            const topRow = document.querySelector('.gallery-row:first-child');
            const bottomRow = document.querySelector('.gallery-row:last-child');
            if (!topRow || !bottomRow) {
                console.error('Gallery rows not found!');
                return;
            }


            topRow.innerHTML = '';
            bottomRow.innerHTML = '';


            if (!galleryImages[galleryIndex]) {
                console.error('Gallery images not found for index:', galleryIndex);
                return;
            }


            galleryImages[galleryIndex].top.forEach(src => {
                const img = createImage(src);
                topRow.appendChild(img);
            });


            galleryImages[galleryIndex].bottom.forEach(src => {
                const img = createImage(src);
                bottomRow.appendChild(img);
            });
        }


        function createImage(src) {
            const img = document.createElement('img');
            img.className = 'gallery-image';
            img.src = src;
            img.alt = 'Gallery Image';
            return img;
        }


        function switchGallery(direction) {
    // Add debug logging
    console.log('switchGallery called with direction:', direction);
    console.log('Current gallery before switch:', currentGallery);


    if(direction === 'next' && currentGallery < totalGalleries - 1) {
        currentGallery++;
        character.x = 0;
    } else if(direction === 'prev' && currentGallery > 0) {
        currentGallery--;
        character.x = window.innerWidth - 100;
    }


    // Add debug logging
    console.log('New gallery index:', currentGallery);
    console.log('Gallery name should be:', galleryNames[currentGallery]);


    loadGallery(currentGallery);
    const galleryNameElement = document.getElementById('gallery-name');
    // Show gallery name with forced display
    if (galleryNameElement) {
        galleryNameElement.style.display = 'block';
        galleryNameElement.style.visibility = 'visible';
        galleryNameElement.textContent = galleryNames[currentGallery];
        galleryNameElement.style.animation = 'fadeIn 0.7s';
        // Force a reflow
        void galleryNameElement.offsetWidth;
       
        // Clear any existing timeout
        if (window.fadeTimeout) {
            clearTimeout(window.fadeTimeout);
        }
       
        // Set new timeout
        window.fadeTimeout = setTimeout(() => {
            galleryNameElement.style.animation = 'fadeOut 0.7s';
            setTimeout(() => {
                galleryNameElement.style.display = 'none';
                galleryNameElement.style.visibility = 'hidden';
            }, 700);
        }, 3000);
    } else {
        console.error('Gallery name element not found!');
    }


    // Update character position
    const charElement = document.getElementById('character');
    if (charElement) {
        charElement.style.left = character.x + 'px';
    }
}


        function checkImageCollision() {
    const images = document.getElementsByClassName('gallery-image');
    const charWidth = 100;
    const charHeight = 100;
    const collisionBuffer = 50; // Smaller detection area around the image


    for(let img of images) {
        const rect = img.getBoundingClientRect();
        if(character.x < rect.right + collisionBuffer &&
           character.x + charWidth > rect.left - collisionBuffer &&
           character.y < rect.bottom + collisionBuffer &&
           character.y + charHeight > rect.top - collisionBuffer) {
            showFullscreen(img.src);
            break;
        }
    }
}


        function showFullscreen(src) {
            const fullscreenView = document.getElementById('fullscreen-view');
            const fullscreenImage = document.getElementById('fullscreen-image');
            fullscreenImage.src = src;
            fullscreenView.style.display = 'block';
            fullscreenView.style.zIndex = '1000';
        }


        // Initial setup
        document.getElementById('character').style.left = character.x + 'px';
        document.getElementById('character').style.top = character.y + 'px';
    </script>
 </body>
 </html>







