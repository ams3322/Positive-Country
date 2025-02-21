<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Country Facts</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            text-align: center;
        }
        .container {
            background-color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            width: 300px;
        }
        button {
            padding: 10px 20px;
            background-color: green;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background-color: darkgreen;
        }
        #fact {
            margin-top: 20px;
            font-size: 18px;
        }
        #countryImage {
            margin-top: 15px;
            max-width: 100%;
            height: auto;
        }
    </style>
</head>
<body>

    <div class="container">
        <button id="factButton">Get Random Country Fact</button>
        <div id="fact"></div>
        <img id="countryImage" src="" alt="" style="display:none;">
    </div>

    <script>
        const facts = {
            "Afghanistan": {
                fact: "Afghanistan is known for its mountainous landscapes and rich cultural heritage.",
                image: "https://i.insider.com/5a454889ec1ade23e7749b89?width=700"
            },
            "Albania": {
                fact: "Albania is famous for its beautiful beaches along the Ionian and Adriatic seas.",
                image: "https://www.thenaturaladventure.com/wp-content/uploads/2023/09/best-time-to-go-to-albania-2.jpg"
            },
            "Algeria": {
                fact: "Algeria is home to part of the Sahara Desert, the largest desert in the world.",
                image: "https://mediaim.expedia.com/destination/1/9c67fd6c233c66d93cb39e498547d155.jpg"
            },
            "Andorra": {
                fact: "Andorra is a small, mountainous country known for its ski resorts.",
                image: "https://media.istockphoto.com/id/1367558023/photo/aerial-view-of-the-city-of-andorra-la-vella-capital-of-andorra.jpg?s=612x612&w=0&k=20&c=iZdmYSGt6NqVsJ_oxRlcXxbXYFe_rTrINbbpHuI648M="
            },
            "Angola": {
                fact: "Angola has a rich cultural history and stunning landscapes.",
                image: "https://images.squarespace-cdn.com/content/v1/5eb85920d2ae880e0ff1526f/99e1ae0b-ce12-4df3-9bac-9893ab7b5c22/23.jpg"
            },
            "Antigua and Barbuda": {
                fact: "This Caribbean nation is known for its white sand beaches and coral reefs.",
                image: "https://secure.s.forbestravelguide.com/img/destinations/Antigua-CreditIR_Stone-iStock.jpg"
            },
            "Argentina": {
                fact: "Argentina is famous for its tango music and the beautiful Iguazu Falls.",
                image: "https://lp-cms-production.imgix.net/2024-08/shutterstock1338447983.jpg?auto=format&q=72&w=1440&h=810&fit=crop"
            },
            "Armenia": {
                fact: "Armenia is one of the oldest countries in the world with a rich cultural heritage.",
                image: "https://mirrorspectator.com/wp-content/uploads/2021/06/15Travel-1.jpeg"
            },
            "Australia": {
                fact: "Australia is known for its Great Barrier Reef and unique wildlife, like kangaroos.",
                image: "https://i.insider.com/5f3424f2988ee31668198a09?width=700"
            },
            "Austria": {
                fact: "Austria is famous for its classical music heritage, especially composers like Mozart.",
                image: "https://cdn.britannica.com/20/191120-050-B6C0B7E9/village-Hallstatt-Alps-Austria.jpg"
            },
            "Azerbaijan": {
                fact: "Azerbaijan is known for its rich cultural history and beautiful landscapes.",
                image: "https://www.journalofnomads.com/wp-content/uploads/2020/01/Azerbaijan-Travel.jpg"
            },
            "Bahamas": {
                fact: "The Bahamas is known for its beautiful beaches and clear waters.",
                image: "https://media-cdn.tripadvisor.com/media/photo-c/1280x250/09/b1/7f/ba/photo0jpg.jpg"
            },
            "Bahrain": {
                fact: "Bahrain is an island country with a rich Islamic history.",
                image: "https://siteselection.com/media/issues/2017/nov/images/FourSeasonsHotel_BahrainBay.jpg"
            },
            "Bangladesh": {
                fact: "Bangladesh is home to the world's largest river delta, the Sundarbans.",
                image: "https://www.state.gov/wp-content/uploads/2019/07/Bangladesh-2109x1406.png"
            },
            "Barbados": {
                fact: "Barbados is known for its vibrant culture and beautiful beaches.",
                image: "https://www.sandals.com/blog/content/images/2024/08/shutterstock_-Mario-Hagen.jpg"
            },
            "Belarus": {
                fact: "Belarus is known for its natural beauty and medieval castles.",
                image: "https://etichotels.com/journal/wp-content/uploads/2024/01/10_Surprising_Facts_About_Belarus-ETIC-Hotels.jpg"
            },
            "Belgium": {
                fact: "Belgium is famous for its chocolates and medieval towns.",
                image: "https://cdn.adventure-life.com/10/76/26/Ghent_Belgium/1300x820.webp"
            },
            "Belize": {
                fact: "Belize is home to the world's second-largest barrier reef.",
                image: "https://dynamic-media-cdn.tripadvisor.com/media/photo-o/16/b5/4c/c8/caye-caulker.jpg?w=600&h=-1&s=1"
            },
            "Benin": {
                fact: "Benin is known for its cultural history and historical sites like Ouidah.",
                image: "https://assets.vogue.com/photos/6600e19f3a39dfd865e9a581/master/w_2560%2Cc_limit/GettyImages-1328533903.jpg"
            },
            "Bhutan": {
                fact: "Bhutan is famous for its monasteries and stunning Himalayan landscapes.",
                image: "https://good-nature-blog-uploads.s3.amazonaws.com/uploads/2022/04/Bhutan-mountain-1-2.jpg"
            },
            "Bolivia": {
                fact: "Bolivia is home to the Salar de Uyuni, the world's largest salt flat.",
                image: "https://www.responsiblevacation.com/imagesClient/17591_1352.jpg"
            },
            "Brazil": {
                fact: "Brazil is famous for its Amazon rainforest and carnival celebrations.",
                image: "https://www.datocms-assets.com/32623/1709134320-rio_de_janeiro_brazil.jpeg"
            },
            "Bulgaria": {
                fact: "Bulgaria has rich traditions in folklore, dance, and music.",
                image: "https://visiteurope.com/wp-content/uploads/Bulgaria.jpg"
            },
            "Cabo Verde": {
                fact: "Cabo Verde is known for its volcanic islands and Creole culture.",
                image: "https://media.cnn.com/api/v1/images/stellar/prod/171214105325-cabo-verde-stock.jpg?q=w_1110,c_fill"
            },
            "Cambodia": {
                fact: "Cambodia is home to the stunning Angkor Wat temple complex.",
                image: "https://upload.wikimedia.org/wikipedia/commons/6/6b/Angkor_Wat_in_2015.jpg"
            },
            "Cameroon": {
                fact: "Cameroon is known for its diverse ecosystems, including rainforests and savannahs.",
                image: "https://africanancestry.com/cdn/shop/articles/cameroon-waterfalls_538032c1-8e0e-48f5-b7e8-13c698e35cbc.jpg?v=1698857961"
            },
            "Canada": {
                fact: "Canada is famous for its vast wilderness and multicultural cities.",
                image: "https://cdn.britannica.com/24/77424-050-4FF80B58/Angkor-Wat-Cambodia.jpg"
            },
            "Chad": {
                fact: "Chad is known for its deserts, lakes, and wildlife.",
                image: "https://journeysbydesign.com/wp-content/uploads/2021/05/Cheres-overview-960x647.jpg"
            },
            "Chile": {
                fact: "Chile is known for its long coastline and stunning Andes mountains.",
                image: "https://cazloyd.com/wp-content/uploads/2023/10/argentina-chile-hero.jpg"
            },
            "China": {
                fact: "China is famous for its ancient history, including the Great Wall and the Terracotta Army.",
                image: "https://natureconservancy-h.assetsadobe.com/is/image/content/dam/tnc/nature/en/photos/g/r/great-wall-of-china.jpg?crop=315%2C0%2C3361%2C1849&wid=4000&hei=2200&scl=0.8404545454545455"
            },
            "Colombia": {
                fact: "Colombia is known for its coffee, tropical rainforests, and Andean mountains.",
                image: "https://www.nomadicdays.org/gallery/HMRwY6wXVHAdoSj/w900/Colombia-pacific.jpg"
            },
            "Costa Rica": {
                fact: "Costa Rica is known for its biodiversity and beautiful beaches.",
                image: "https://www.wildernesstravel.com/wp-content/uploads/2023/06/arenal-volcano-costa-rica-1680x1063.jpg"
            },
            "Croatia": {
                fact: "Croatia is known for its stunning coastline along the Adriatic Sea.",
                image: "https://cruisecroatia.com/wp-content/uploads/2023/06/Stiniva-Cove.jpg"
            },
            "Cuba": {
                fact: "Cuba is famous for its vibrant culture, beautiful beaches, and historic architecture.",
                image: "https://media.cntraveler.com/photos/5cf96d2ef9ef7cc71fa6f0b5/1:1/w_2670,h_2670,c_limit/Havanna,-Cuba_GettyImages-649524172.jpg"
            },
            "Denmark": {
                fact: "Denmark is known for being one of the happiest countries in the world.",
                image: "https://www.ambassadorcruiseline.com/_astro/1200x675_Z1EJv3s.webp"
            },
            "Dominica": {
                fact: "Dominica is an island paradise known for its volcanic mountains and hot springs.",
                image: "https://media.cntraveler.com/photos/63d93883ff7e4ac51f2db422/16:9/w_2560%2Cc_limit/Secret%2520Bay_Aerial%2520View%2520of%2520Secret%2520Bay.jpg"
            },
            "Ecuador": {
                fact: "Ecuador is home to the Galápagos Islands, a UNESCO World Heritage site.",
                image: "https://www.lastfrontiers.com/imagestore/ecuador/EC1096EPB37_cotopaxi.jpg"
            },
            "Egypt": {
                fact: "Egypt is home to the ancient pyramids of Giza and the Sphinx.",
                image: "https://res.cloudinary.com/jerrick/image/upload/v1674459796/63ce3a946712d5001d07ddcd.jpg"
            },
            "El Salvador": {
                fact: "El Salvador is the smallest country in Central America but offers great beaches and volcanoes.",
                image: "https://elsalvador.travel/system/wp-content/uploads/2024/06/centro05.jpg"
            },
            "Fiji": {
                fact: "Fiji is a popular tourist destination known for its tropical islands and coral reefs.",
                image: "https://dynamic-media-cdn.tripadvisor.com/media/photo-o/07/32/1d/8a/likuliku-lagoon-resort.jpg?w=600&h=400&s=1"
            },
            "Finland": {
                fact: "Finland is famous for its northern lights and being one of the happiest countries in the world.",
                image: "https://th-thumbnailer.cdn-si-edu.com/knjBx4mV_4p2XfJgochLL-9k1C0=/fit-in/1600x0/filters:focal(2168x1721:2169x1722)/https://tf-cmsv2-journeys-media.s3.amazonaws.com/filer_public/9a/99/9a99800a-c927-4c32-9cb4-e27a0d271b2b/fin_northern_lights_ist_163729324.jpg"
            },
            "France": {
                fact: "France is known for its iconic Eiffel Tower and world-renowned cuisine.",
                image: "https://sjmc.gov.au/wp-content/uploads/2017/11/Shutterstock_111362132-Eiffel-Tower-and-Paris-1600x950.jpg"
            },
            "Georgia": {
                fact: "Georgia is known for its stunning landscapes and ancient winemaking traditions.",
                image: "https://www.atlys.com/_next/image?url=https%3A%2F%2Fimagedelivery.net%2FW3Iz4WACAy2J0qT0cCT3xA%2Fdidi%2Farticles%2Fa2u9jcf45jepokeb5xx2uy8i%2Fpublic&w=1920&q=75"
            },
            "Germany": {
                fact: "Germany is famous for its engineering excellence, beer culture, and history.",
                image: "https://images.ctfassets.net/wv75stsetqy3/YlehZx0vhKERIOF5xKXBs/84e8fc7b0e165467129768c4140aadf0/Pros_and_Cons_of_Living_in_Germany.jpg?q=60&fit=fill&fm=webp"
            },
            "Ghana": {
                fact: "Ghana is known for its vibrant culture and history of gold mining.",
                image: "https://media.cnn.com/api/v1/images/stellar/prod/201009100355-11-ghana-things-to-do.jpg?q=w_1600,h_965,x_0,y_0,c_fill/h_447"
            },
            "Greece": {
                fact: "Greece is famous for its ancient history, including the Parthenon and ancient Olympic Games.",
                image: "https://images.ctfassets.net/wv75stsetqy3/18jOEJrhKM7WA81nkCKZV8/6f70df258ed1233d5c3a8e3f01298b06/Greece.jpg?q=60&fit=fill&fm=webp"
            },
            "Guatemala": {
                fact: "Guatemala is home to the ancient Mayan ruins of Tikal.",
                image: "https://media.cntraveler.com/photos/612146f9ae88a6ec4f841bf9/16:9/w_2560%2Cc_limit/LICENSE_Mari%25CC%2581a%2520Mercedes%2520Coroy-Guatemala-_(c)%2520Getty%2520Images_CNT%2520UK_Sophie%2520Knight.jpeg"
            },
            "Guyana": {
                fact: "Guyana is famous for its diverse ecosystems and natural beauty.",
                image: "https://worldlyadventurer.com/wp-content/uploads/2020/04/Guyana-Kaieteur-Falls-5.jpg"
            },
            "Haiti": {
                fact: "Haiti is known for its rich history and vibrant culture, with a strong influence of African traditions.",
                image: "https://www.telegraph.co.uk/content/dam/Travel/leadAssets/29/86/haiti-Citadel-on-P_2986485a.jpg?imwidth=680"
            },
            "Honduras": {
                fact: "Honduras is home to the ancient Mayan ruins of Copán and offers beautiful beaches on the Caribbean coast.",
                image: "https://www.exoticca.com/_next/image?url=https%3A%2F%2Fres.cloudinary.com%2Fexoticca%2Fimage%2Fupload%2Fc_limit%2Cf_auto%2Cq_auto%3Aeco%2Cw_1280%2Fv1%2FCountry%2FHONDURAS%2FHonduras-Roatan_awnh9q&w=3840&q=75"
            },
            "Hungary": {
                fact: "Hungary is known for its stunning architecture, historic cities, and thermal baths.",
                image: "https://i.natgeofe.com/k/e965ea18-80fa-4205-a1df-3ec327ddb567/hungary-budapest.jpg"
            },
            "Iceland": {
                fact: "Iceland is famous for its dramatic landscapes, including glaciers, volcanoes, and geothermal hot springs.",
                image: "https://cdn.britannica.com/06/171306-050-C88DD752/Aurora-borealis-peninsula-Snaefellsnes-Iceland-March-2013.jpg"
            },
            "India": {
                fact: "India is known for its rich cultural diversity, vibrant festivals, and iconic landmarks like the Taj Mahal.",
                image: "https://cdn.mos.cms.futurecdn.net/3FnczamRyWU6MvRMEXWaGD-1200-80.jpg"
            },
            "Indonesia": {
                fact: "Indonesia is an archipelago of thousands of islands and is known for its stunning beaches and biodiversity.",
                image: "https://media.cntraveler.com/photos/59404f9157d01262a807f8c9/4:3/w_4540,h_3405,c_limit/GettyImages-175386102.jpg"
            },
            "Iran": {
                fact: "Iran is known for its ancient history, rich cultural heritage, and the Persian Empire.",
               image: "https://i.natgeofe.com/n/96945883-98fe-406d-b6cc-92ec1e5e9bd3/travertine-terrace-badab-e-surt-iran.jpg"
            },
            "Iraq": {
                fact: "Iraq is home to one of the world's oldest civilizations, the Sumerians, and the cradle of early human history.",
                image: "https://beyondthebucketlist.co/wp-content/uploads/2022/09/DSC_0570.jpg"
            },
            "Ireland": {
                fact: "Ireland is famous for its lush landscapes, castles, and rich history of folklore and traditions.",
                image: "https://th-thumbnailer.cdn-si-edu.com/hjWAJF9AlAyyPyA6bC0ai3VYmYg=/fit-in/1600x0/https://tf-cmsv2-journeys-media.s3.amazonaws.com/filer/b5/d8/b5d8e406-fd93-4b83-8575-82996413dbbd/ire_cliffsofmoher_ist_000039133428_large_ccforweb.jpg"
            },
            "Israel": {
                fact: "Israel is a country of historical significance, home to sacred sites for Jews, Christians, and Muslims.",
                image: "https://cdn-us0.puzzlegarage.com/img/puzzle/c/1868_preview.v3.jpg"
            },
            "Italy": {
                fact: "Italy is known for its art, architecture, cuisine, and historic landmarks such as the Colosseum.",
                image: "https://www.affordableluxurytravel.co.uk/blog/wp-content/uploads/2023/06/italy-1.jpg"
            },
            "Jamaica": {
                fact: "Jamaica is famous for its music, particularly reggae, and its beautiful beaches.",
                image: "https://apiimg.iberostar.com/uploads/image/37580/crops/16:9/720/image.jpeg"
            },
            "Japan": {
                fact: "Japan is known for its technological advancements, rich traditions, and beautiful cherry blossoms.",
                image: "https://www.celebritycruises.com/blog/content/uploads/2021/03/what-is-japan-known-for-mt-fuji-hero-1920x890.jpg"
            },
            "Kazakhstan": {
                fact: "Kazakhstan is known for its vast steppes, rich mineral resources, and history of nomadic cultures.",
                image: "https://media-cdn.tripadvisor.com/media/attractions-splice-spp-674x446/0c/08/a3/c5.jpg"
            },
            "Kenya": {
                fact: "Kenya is famous for its wildlife, including the Big Five, and its beautiful landscapes.",
                image: "https://res.cloudinary.com/sagacity/image/upload/c_crop,h_3029,w_4540,x_0,y_0/c_limit,dpr_auto,f_auto,fl_lossy,q_80,w_1080/shutterstock_784433020_xsnwky.jpg"
            },
            "North Korea": {
                fact: "North Korea is known for its strict regime and its secretive society.",
                image: "https://i.natgeofe.com/k/8c2c618a-3daa-40dc-9ee4-32f15b811e2f/City_N-Korea_KIDS_0521_3x2.jpg"
            },
            "South Korea": {
                fact: "South Korea is famous for its technology, pop culture (K-Pop), and vibrant cities like Seoul.",
                image: "https://exodus-website.s3.amazonaws.com/uploads/2024/10/Main-image-8-1024x683.jpg"
            },
            "Laos": {
                fact: "Laos is known for its Buddhist culture and stunning waterfalls.",
                image: "https://lp-cms-production.imgix.net/2024-10/shutterstockRF208712644.jpg?auto=format&q=72&fit=crop"
            },
            "Lebanon": {
                fact: "Lebanon is known for its rich history, diverse culture, and Mediterranean cuisine.",
                image: "https://www.ispionline.it/wp-content/uploads/2018/05/beirut-lebanon-614628-scaled.jpg"
            },
            "Liechtenstein": {
                fact: "Liechtenstein is one of the smallest countries in the world, known for its alpine landscapes.",
                image: "https://www.lower-austria.info/images/qxwxqur!ome-/df81192493df52aabfb9025c4e7aab95.jpg"
            },
            "Lithuania": {
                fact: "Lithuania is known for its rich history and beautiful medieval architecture.",
               image: "https://imageio.forbes.com/blogs-images/jimdobson/files/2018/07/1-1.jpg?height=430&width=645&fit=bounds"
            },
            "Madagascar": {
                fact: "Madagascar is famous for its unique wildlife, such as lemurs and other endemic species.",
                image: "https://www.telegraph.co.uk/content/dam/Travel/2017/june/cycling%20131314241_Cultura%20Exclusive_Madagascar.jpg?imwidth=680"
            },
            "Malaysia": {
                fact: "Malaysia is known for its tropical rainforests, pristine beaches, and vibrant cities like Kuala Lumpur.",
                image: "https://i.natgeofe.com/k/8dc7401d-fac9-43c5-a6d4-d056401f7779/kuala-lumpur.jpg?wp=1&w=1084.125&h=721.875"
            },
            "Maldives": {
                fact: "The Maldives is famous for its turquoise waters, coral reefs, and luxury resorts.",
                image: "https://media.glamourmagazine.co.uk/photos/6645c61272a9b47788824369/16:9/w_1920,h_1080,c_limit/Nova%20Hotel%20Review%20160524%203-4-SCALED%20COPY.jpg"
            },
            "Mexico": {
                fact: "Mexico is rich in culture, history, and beautiful landscapes, with ancient Mayan ruins and stunning beaches.",
                image: "https://afar.brightspotcdn.com/dims4/default/94017a2/2147483647/strip/false/crop/3000x1500+0+0/resize/1486x743!/quality/90/?url=https%3A%2F%2Fk3-prod-afar-media.s3.us-west-2.amazonaws.com%2Fbrightspot%2F22%2Fa3%2Fbf9b1d384ca8a9dcb732491dfadf%2Ftravelguide-mexicocity-ramiroreynajr.jpg"
            },
            "Moldova": {
                fact: "Moldova is known for its stunning vineyards and rich agricultural history.",
                image: "https://www.travelguide.net/media/c/md.jpeg"
            },
            "Monaco": {
                fact: "Monaco is famous for its luxurious casinos, beaches, and as the home of the prestigious Formula 1 Grand Prix.",
                image: "https://www.monaco-tribune.com/wp-content/uploads/2020/11/monaco-covid-19-e1606478044724.jpg"
            },
            "Morocco": {
                fact: "Morocco is known for its vibrant markets, ancient palaces, and stunning desert landscapes.",
                image: "https://www.costsavertour.com/media/j1zfuxeh/blue-city-chefchaouen-tangier-morocco-1.jpg?center=0.5%2C0.5&format=webp&mode=crop&width=1200&height=1200&quality=80"
            },
            "Nepal": {
                fact: "Nepal is famous for the Himalayas, including Mount Everest, the tallest mountain in the world.",
                image: "https://cdn.britannica.com/78/155378-050-838B4322/Himalayas-Nepal.jpg"
            },
            "Netherlands": {
                fact: "The Netherlands is famous for its beautiful windmills, tulip fields, and cycling culture.",
                image: "https://www.holland.com/upload_mm/2/3/6/75601_fullimage_aerial%20view%20of%20downtown%20amsterdam%2C%20the%20netherlands%20during%20a%20dramatic%20beautiful%20sunset%20foto%20repistu%20via%20istock.jpg"
            },
            "New Zealand": {
                fact: "New Zealand is known for its stunning landscapes and outdoor adventure opportunities, from beaches to mountains.",
                image: "https://www.newzealand.com/assets/Digital-Platform-Use-Only/TBD-assets-on-nonlistings/img-1574411693-934-30755-p-2BF67817-CC86-C995-EDE7B703CBD315EE-2544003__aWxvdmVrZWxseQo_FocalPointCropWzQ0MCw3NDcsNTAsNTAsNzUsImpwZyIsNjUsMi41XQ.jpeg"
            },
            "Nicaragua": {
                fact: "Nicaragua is famous for its beautiful lakes, volcanoes, and charming colonial cities.",
                image: "https://www.iadb.org/sites/default/files/styles/landscape_2x1_768000_768x384_100/public/2023-03/%E2%80%AF1.6.19-banner-BID-Nicaragua-928438734.jpg?h=b6cd0f36&itok=yWGXaKvr"
            },
            "Niger": {
                fact: "Niger is known for its beautiful desert landscapes and as a major center for uranium mining.",
                image: "https://www.blackpast.org/wp-content/uploads/Niamey-Niger.jpg"
            },
            "Nigeria": {
                fact: "Nigeria is a country with rich cultural diversity and a booming film industry, known as Nollywood.",
                image: "https://lh3.googleusercontent.com/ci/AL18g_SPUfELqC9KuuBVFpctar4xRA3Af23HKu8vKLugO72EmlKEdkQrAvFaDDVbN_nDPQBZAEfoswM=s1200"
            },
            "Norway": {
                fact: "Norway is famous for its majestic fjords, outdoor adventures, and northern lights.",
                image: "https://i0.wp.com/globalgrasshopper.com/wp-content/uploads/2014/06/most-beautiful-places-to-visit-in-Norway-1.jpg?resize=840%2C578&ssl=1"
            },
            "Oman": {
                fact: "Oman is known for its beautiful desert landscapes and rich cultural heritage.",
                image: "https://www.state.gov/wp-content/uploads/2023/07/shutterstock_1050310166-scaled.jpg"
            },
            "Pakistan": {
                fact: "Pakistan is rich in history, culture, and has diverse landscapes ranging from mountains to deserts.",
                image: "https://i.natgeofe.com/n/6df2d841-921a-481e-84c2-1a0649e785a3/hunza-valley-pakistan.jpg"
            },
            "Panama": {
                fact: "Panama is famous for the Panama Canal, which connects the Atlantic and Pacific Oceans.",
                image: "https://www.essence.com/wp-content/uploads/2024/04/6540_221203_Sofitel-scaled.jpg"
            },
            "Paraguay": {
                fact: "Paraguay is famous for its rivers and lakes, along with its vibrant indigenous cultures.",
                image: "https://idsb.tmgrup.com.tr/ly/uploads/images/2022/04/10/197704.jpg"
            },
            "Peru": {
                fact: "Peru is home to the famous Machu Picchu, an ancient Incan city set high in the Andes Mountains.",
                image: "https://images.myguide-cdn.com/content/1/large/regional-information-peru-632307.jpg"
            },
            "Philippines": {
                fact: "The Philippines is known for its beautiful islands, clear waters, and rich biodiversity.",
                image: "https://i.natgeofe.com/n/04505c35-858b-4e95-a1a7-d72e5418b7fc/steep-karst-cliffs-of-el-nido-in-palawan.jpg"
            },
            "Poland": {
                fact: "Poland has a rich history, including being the birthplace of composer Frederic Chopin.",
                image: "https://statemag.state.gov/wp-content/uploads/2023/03/0423pom-1-scaled.jpg"
            },
            "Portugal": {
                fact: "Portugal is famous for its historic architecture, port wine, and stunning coastline.",
                image: "https://imageresizer.yachtsbt.com/blog/images/Portugal/iStock-687689468.jpg?method=crop&width=1700&height=1275&format=jpeg"
            },
            "Russia": {
                fact: "Russia is the largest country in the world, spanning Eastern Europe and northern Asia.",
                image: "https://i.natgeofe.com/k/415419c5-3768-4c8f-8697-f90de7a6075b/russia-st-basils.jpg?wp=1&w=1084.125&h=609"
            },
            "Saudi Arabia": {
                fact: "Saudi Arabia is famous for being home to the two holiest cities in Islam, Mecca and Medina.",
                image: "https://media.cnn.com/api/v1/images/stellar/prod/231006161801-01-body-saudi-arabia-tourism-basics-riyadh.jpg?q=w_1110,c_fill"
            },
            "Serbia": {
                fact: "Serbia is known for its cultural heritage, including medieval monasteries and the vibrant capital, Belgrade.",
                image: "https://lp-cms-production.imgix.net/2023-03/shutterstockRF_220992322.jpg"
            },
            "Singapore": {
                fact: "Singapore is famous for its futuristic skyline, clean streets, and innovative architecture.",
                image: "https://i.natgeofe.com/k/95d61645-a0c7-470f-b198-74a399dd5dfb/singapore-city_2x1.jpg"
            },
            "Slovakia": {
                fact: "Slovakia is known for its medieval castles and the beautiful High Tatras mountains.",
                image: "https://www.lot.com/content/dam/lot/lot-com/destination-photos/słowacja/bratislava-3.coreimg.jpg/1723629181269/bratislava-3.jpg"
            },
            "Somalia": {
                fact: "Somalia is famous for its beautiful coastline, including the longest coastline in mainland Africa.",
                image: "https://i.ytimg.com/vi/nKmRS__Hq1s/sddefault.jpg"
            },
            "South Africa": {
                fact: "South Africa is known for its stunning landscapes, including safaris in Kruger National Park and the iconic Table Mountain.",
                image: "https://www.africa.com/wp-content/uploads/2019/01/Webp.net-compress-image-12.jpg"
            },
            "South Sudan": {
                fact: "South Sudan, one of the newest countries, is known for its diverse ethnic groups and rich natural resources.",
                image: "https://www.ft.com/__origami/service/image/v2/images/raw/ftcms%3Ad99b39aa-f430-4e34-93a9-2cb3947d8e8b?source=next-article&fit=scale-down&quality=highest&width=1440&dpr=1"
            },
            "Spain": {
                fact: "Spain is famous for its vibrant culture, historic cities, and iconic landmarks like the Sagrada Familia.",
                image: "https://hips.hearstapps.com/hmg-prod/images/spain-holiday-destinations-lead-girona-pol-albarra-n-1675292136.jpg?crop=0.654xw:1.00xh;0.0913xw,0&resize=1200:*"
            },
            "Sri Lanka": {
                fact: "Sri Lanka is known for its stunning beaches, ancient ruins, and diverse wildlife.",
                image: "https://static01.nyt.com/images/2019/02/03/travel/03frugal-srilanka01/merlin_148552275_74c0d250-949c-46e0-b8a1-e6d499e992cf-superJumbo.jpg"
            },
            "Sweden": {
                fact: "Sweden is known for its stunning natural landscapes, including forests, lakes, and the Northern Lights.",
                image: "https://cms.sweden.se/app/uploads/2024/10/northern-lights.jpg"
            },
            "Switzerland": {
                fact: "Switzerland is famous for its scenic mountains, luxury watches, and being home to the Red Cross.",
                image: "https://keystoneacademic-res.cloudinary.com/image/upload/v1733331993/Switzerland_rkswd8.png"
            },
            "Taiwan": {
                fact: "Taiwan is famous for its mountainous terrain, bustling cities, and vibrant night markets.",
                image: "https://travelbuddieslifestyle.com/wp-content/uploads/2023/10/IMG_9236-scaled.jpg"
            },
            "Tajikistan": {
                fact: "Tajikistan is known for its rugged mountain landscapes, particularly the Pamirs, often called 'The Roof of the World'.",
                image: "https://cdn.britannica.com/60/96060-050-EEA73BE2/peaks-Pamirs-Tajikistan.jpg"
            },
            "Tanzania": {
                fact: "Tanzania is home to Mount Kilimanjaro, the highest mountain in Africa, and the Serengeti National Park.",
                image: "https://www.state.gov/wp-content/uploads/2018/11/Tanzania-e1555938157355-2501x1406.jpg"
            },
            "Thailand": {
                fact: "Thailand is known for its stunning temples, vibrant cities, and beautiful islands like Phuket and Koh Samui.",
                image: "https://images.ctfassets.net/wv75stsetqy3/DaKdXY2tkQGWeVQiCbSx7/ac01166282697e4e0cafb99180d35cd1/Thailand_Featured.jpg?q=60&fit=fill&fm=webp"
            },
            "Turkey": {
                fact: "Turkey is famous for its unique blend of cultures, rich history, and landmarks like the Hagia Sophia and Pamukkale.",
                image: "https://static.independent.co.uk/2023/12/15/09/iStock-903934818.jpg?width=1200"
            },
            "Turkmenistan": {
                fact: "Turkmenistan is known for its vast deserts, ancient ruins, and the eerie Door to Hell, a burning gas crater.",
                image:"https://www.state.gov/wp-content/uploads/2023/07/shutterstock_1904359585v2.jpg" 
            },
            "Uganda": {
                fact: "Uganda is known for its rich wildlife, including the endangered mountain gorillas in Bwindi Impenetrable Forest.",
                image: "https://www.andbeyond.com/wp-content/uploads/sites/5/faq-uganda.jpg"
            },
            "Ukraine": {
                fact: "Ukraine is known for its fertile farmland, beautiful landscapes, and the historic city of Kyiv.",
                image: "https://i.natgeofe.com/k/29ce0d21-6863-4fe5-a0ed-082ad307161c/Kyiv_Ukraine_0322_4x3.jpg"
            },
            "United Arab Emirates": {
                fact: "The United Arab Emirates is famous for its modern architecture, luxury shopping, and iconic landmarks like the Burj Khalifa.",
                image: "https://www.state.gov/wp-content/uploads/2019/04/UAE-2109x1406.jpg"
            },
            "United Kingdom": {
                fact: "The United Kingdom is famous for its rich history, landmarks like the Tower of London, and global cultural influence.",
                image: "https://i0.wp.com/cms.babbel.news/wp-content/uploads/2018/02/UKLanguages.png?resize=1200,630"
            },
            "United States": {
                fact: "The United States is known for its cultural diversity, technological innovation, and iconic landmarks such as the Statue of Liberty.",
                image: "https://www.hellolanding.com/blog/wp-content/uploads/2024/02/Yosemite-National-Park-USA-1024x683.jpg"
            },
            "Uruguay": {
                fact: "Uruguay is famous for its beautiful beaches, rich culture, and being the first country to legalize marijuana.",
                image: "https://images.squarespace-cdn.com/content/v1/52efc94ae4b01409c74273d6/1585760486953-KVGMFRIB0WUT0KZ3UEA5/montevideo_grande.jpg"
            },
            "Uzbekistan": {
                fact: "Uzbekistan is home to many important cultural and historical sites, including ancient cities like Samarkand and Bukhara.",
                image: "https://ichef.bbci.co.uk/ace/standard/976/cpsprodpb/159F7/production/_130876588_gettyimages-638640833.jpg"
            },
            "Venezuela": {
                fact: "Venezuela is known for its stunning Angel Falls, the world's highest uninterrupted waterfall.",
                image: "https://www.worldatlas.com/r/w1200/upload/9d/f0/92/shutterstock-176494907.jpg"
            },
            "Vietnam": {
                fact: "Vietnam is famous for its stunning landscapes, such as Ha Long Bay, and its rich history and cuisine.",
                image: "https://www.datocms-assets.com/32623/1705943597-vietnam_halong_bay.jpeg"
            },
            "Yemen": {
                fact: "Yemen is home to one of the most ancient civilizations, with its old city of Sana'a being a UNESCO World Heritage site.",
                image: "https://www.ft.com/__origami/service/image/v2/images/raw/ftcms%3Ab98f1c68-9694-4453-9916-78e712293fd0?source=next-article&fit=scale-down&quality=highest&width=1440&dpr=1"
            },
            "Zimbabwe": {
                fact: "Zimbabwe is known for its breathtaking landscapes, including the famous Victoria Falls and the ancient ruins of Great Zimbabwe.",
                image: "https://good-nature-blog-uploads.s3.amazonaws.com/uploads/2023/11/AdobeStock_442349111.jpg"
            }
        };


        function getRandomFact() {
            const countryNames = Object.keys(facts);
            const randomCountry = countryNames[Math.floor(Math.random() * countryNames.length)];
            const fact = facts[randomCountry].fact;
            const image = facts[randomCountry].image;
            
            document.getElementById("fact").textContent = fact;
            document.getElementById("countryImage").src = image;
            document.getElementById("countryImage").style.display = "block";
        }

        document.getElementById("factButton").addEventListener("click", getRandomFact);
    </script>
</body>
</html> 
