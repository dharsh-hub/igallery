# Ex.08 Design of Interactive Image Gallery
## Date:24/12/2024

## AIM:
To design a web application for an inteactive image gallery with minimum five images.

## DESIGN STEPS:

### Step 1:
Clone the github repository and create Django admin interface.

### Step 2:
Change settings.py file to allow request from all hosts.

### Step 3:
Use CSS for positioning and styling.

### Step 4:
Write JavaScript program for implementing interactivity.

### Step 5:
Validate the HTML and CSS code.

### Step 6:
Publish the website in the given URL.

## PROGRAM :

```

<html lang="en">
<head>
    
    <title>Interactive Photo Gallery</title>
    <style>
        body {
            background-color: #222;
            font-family: 'Open Sans', sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
        }

        .header {
            text-align: center;
            color: white;
            font-size: 24px;
            font-weight: bold;
            margin-bottom: 20px;
        }

        .gallery-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 15px;
            padding: 20px;
            max-width: 1200px;
            width: 100%;
            animation: fadeIn 1s ease-in-out;
        }

        .gallery-item {
            position: relative;
            overflow: hidden;
            border-radius: 10px;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
        }

        .gallery-item img {
            width: 100%;
            height: auto;
            border-radius: 10px;
            transition: transform 0.3s ease, filter 0.3s ease;
        }

        .gallery-item img:hover {
            transform: scale(1.1);
            filter: brightness(0.8);
            cursor: pointer;
        }

        .caption {
            position: absolute;
            bottom: 8px;
            left: 8px;
            background-color: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 12px;
            text-align: center;
            width: calc(100% - 16px);
        }

        .modal {
            display: none;
            position: fixed;
            z-index: 1;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            margin: auto;
            display: block;
            width: 80%;
            max-width: 600px;
            border-radius: 10px;
        }

        .close {
            position: absolute;
            top: 10px;
            right: 20px;
            color: white;
            font-size: 30px;
            cursor: pointer;
        }

        .modal-description {
            color: white;
            text-align: center;
            padding: 10px;
            font-size: 16px;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body>

    <div class="header">Vietnam Gallery</div>

    <div class="gallery-container">
        <div class="gallery-item">
            <img src="da nang.png" alt="Da Nang" 
            data-description="No other city represents Vietnam's boom better than Da Nang.
            It's become a gleaming, modern tourist magnet, complete with condos, theme parks, and brand-new resorts.
            But the city's earlier charm is still present, including laid-back, friendly locals and incredible street eats. 
            After you've stuffed yourself with a bowl of Mi Quang and Banh Mi Ba Lan, walk it off by exploring the limestone caves and Buddhist grottos of the Marble Mountains.
            Make an escape to the surreal mountain resort of Ba Na Hills, where the majestic Golden Bridge welcomes you with open palms." >
            <div class="caption">Da Nang</div>
        </div>
        <div class="gallery-item">
            <img src="ha long bay.png" alt="Ha Long Bay"  
            data-description="For many, the seascape of Ha Long Bay is synonymous with Vietnam. Cruises sail emerald green waters among thousands of rugged islands and islets,
            stopping at spectacular caves through which visitors can wander, viewing impressive, centuries-old formations.
            Ha Long Bay's mystical beauty has made it a bucket list attraction within the country, but it's still possible to find secluded corners to call your own. " >
            <div class="caption">HA LONG BAY</div>
        </div>
        <div class="gallery-item">
            <img src="hanoi.png" alt="hanoi" 
            data-description="Founded over 1000 years ago, Vietnam’s capital city is rich in history, with the streets of its rambling Old Quarter dating back to the 14th century. 
            Wandering these tree-lined lanes past crumbling colonial facades will transport you back in time. 
            However, today's Hanoi is about much more than the past. The ancient city is being invigorated with modern cafes, world-class restaurants, and cool art galleries.">
            <div class="caption">HANOI</div>
        </div>
        <div class="gallery-item">
            <img src="sapa countryside.png" alt="Sapa Countryside" 
            data-description="Sapa town stands at the head of a deep valley of magnificent rice terraces that are still farmed today as they have been for centuries. 
            Backdrops don't get much more spectacular. Enticing ribbons of road lead the eye down to the valley floor, white-water rivers rush among rice fields, 
            and lush green mountains stretch into the distance as far as the eye can see. The highest peak in the region, Mount Fansipan, crowns the ragged ridge line high above town.">
            <div class="caption">SAPA COUNTRYSIDE</div>
        </div>
        <div class="gallery-item">
            <img src="nha trang.png" alt="Nha Trang" 
            data-description="Perched on a pristine stretch of the southern coast, Nha Trang is a playground for sunseekers. Days here are spent dining on delicious seafood, 
            snorkelling around stunning islands, and partying on the sand after dark. Nha Trang lays claim to some of the country's finest luxury resorts and thrilling watersports. 
            Despite the development boom, colourful fishing villages and serene riverside restaurants are just a stone's throw away.">
            <div class="caption">NHA TRANG</div>
        </div>
        <div class="gallery-item">
            <img src="cu chi tunnels.png" alt="Cu Chi Tunnels" 
            data-description="The tunnels were dug during the Vietnam War by Viet Cong soldiers as a way to move undetected and launch surprise attacks. 
            Experience the tight squeeze firsthand by crawling through the tunnels, and fire assault rifles at the shooting range after. ">
            <div class="caption">CU CHI TUNNELS</div>
        </div>
        <div class="gallery-item">
            <img src="ba be national park.png" alt="Ba be National Park" 
            data-description="Ba Be National Park, often referred to as the Ba Be Lake, is situated in Bac Can Province, about 240 km from Hanoi. 
            It spans over 23,000 hectares of beautiful waterfalls, deep rivers, valleys, lakes and caves, all set amongst towering peaks. 
            The whole area is home to many ethnic communities too.">
            <div class="caption">BA BE NATIONAL PARK</div>
        </div>
    </div>

    <div class="modal" id="modal">
        <span class="close" id="close">&times;</span>
        <img class="modal-content" id="modal-img">
        <div class="modal-description" id="modal-description"></div>
    </div>

    <script>
        const images = document.querySelectorAll('.gallery-item img');
        const modal = document.getElementById('modal');
        const modalImg = document.getElementById('modal-img');
        const modalDescription = document.getElementById('modal-description');
        const closeBtn = document.getElementById('close');

        images.forEach((image) => {
            image.addEventListener('click', () => {
                modal.style.display = 'flex';
                modalImg.src = image.src;
                modalDescription.textContent = image.getAttribute('data-description');
            });
        });

        closeBtn.addEventListener('click', () => {
            modal.style.display = 'none';
        });
    </script>
</body>
</html>

```

## OUTPUT:

![alt text](gallery/1.png)
![alt text](gallery/2.png)
![alt text](gallery/3.png)
![alt text](gallery/4.png)
![alt text](gallery/5.png)
![alt text](gallery/6.png)
![alt text](gallery/7.png)
![alt text](gallery/8.png)

## RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
