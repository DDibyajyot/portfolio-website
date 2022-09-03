<script>
	import { slide } from 'svelte/transition';
    import { quintInOut } from 'svelte/easing';
    import Nav from './Nav.svelte'
    import Card from './Card.svelte'
    let subp = ""
    	function swipeUp(node, { duration }) {
		return {
			duration,
			css: t => {
				const eased = quintInOut(t);
				return `
                    transform: translate3d(0,${(1-eased)*100}%,0);
                    `
			}
		};
    }
    function handleSub(event){
        subp = event.detail.path
    }
    function handleSubClose(){
        subp = ""
    }
</script>

    <div transition:swipeUp={{duration: 800 }}   class="panel">
        <a class="close" href="#home" > 
            <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.25" stroke-linecap="round" stroke-linejoin="round" class="feather feather-x"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg>
        </a>
        {#if subp != ""}
        <a class="close c2" href="#projects" on:click={handleSubClose}> 
           <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.25" stroke-linecap="round" stroke-linejoin="round" class="feather feather-chevron-left"><polyline points="15 18 9 12 15 6"></polyline></svg> </a>
        {/if}
        <h2>Projects{#if subp != ""}/{subp}{/if}</h2>
        <article >

                <Card name={"CAA"} img={"caa.png"} on:sub={handleSub} bind:maybe={subp} >
                    <p slot="desc">
                        This was my first co-op lasting from May to August 2022!
                        <br><br> 
                        I worked as a Full-Stack Developer at CAA Club Group where I architected and rebuilt the employee support portal.
                        This also had the vendor management system integrated into it for easier access to data when the employees need it for contact.
                        This portal supported over 2500 employees, helped them to manage their data such as username/password, manage vendor status (such as towing services), enable them to block vendors, add/delete/edit vendors and emergency contact information.
                        <br><br>
                        I also led the emergency response portal rebuilding which enabled CAA users to request emergency services for accidents and other emergencies on the road.
                        This led to a faster response by over 225% over the previous model.
                        <br><br>
                        I used Next.js predominantly for the frontend, and used MuleSoft and SoapUI to create the REST APIs for CRUD functionalities. 
                        <br><br> 
                        Technologies used: Next.js, React, MuleSoft, SoapUI, TortoiseGit, Axios.
                        <br><br>
                    </p>
                </Card>

                <Card name={"Portfolio"} img={"thissite.png"} url={"deepamdibyajyot.me"} on:sub={handleSub} bind:maybe={subp}>
                    <p slot="desc">
                        This is the spacey-themed portfolio website you are currently on! 
                        <br><br>
                        Loved using Svelte for this!
                        <br><br>
                        Technologies used: Svelte, JavaScript.
                        <br><br>
                    </p>
                </Card>
           
                <Card name={"PriceMatch"} img={"pricematch.jpeg"} url={"https://devpost.com/software/pricematch"} on:sub={handleSub} bind:maybe={subp} >
                <p slot="desc">
                PriceMatch throws the ball back into the consumer's court by helping compare prices for any item. 
                Simply take a picture of the product and you get a list of stores and prices at your fingertips.
                
                <br>
                  <br>
                This was built for HackTheNorth 2021, where as international students, we suddenly found ourselves with a new pricing system without anything to compare to.
                Thus PriceMatch was born. We created a web app that allows users to take a picture of a product and get a list of stores and prices. This was enabled by the model
                we made in TensorFlow to recognize the product and the Google Cloud Vision API to get the price. We also used the Google Maps API to get the store locations.
                Using the database of prices and products, we compared the prices and thus showed the top 3 stores with the lowest prices.
                <br>
                  <br>
                It is built using React for the frontend, and Flask for API and Firebase for the basic backend. TensorFlow was used for making the training model. More info <a href="https://devpost.com/software/pricematch">here</a>.
                <br><br>
                Technologies used: React, Python, JavaScript, Flask, TensorFlow, Firebase.
                <br><br>
                </p>
                </Card>
                
                <Card name={"EDeasy"} img={"Edeasy.jpeg"} url={"https://devpost.com/software/edeasy"} on:sub={handleSub} bind:maybe={subp}>
                    <p slot="desc">
                        EDeasy was a project that I'm quite proud of. EDeasy helps accumulate all the free open-source educational materials that are available on the web and then organizes them according to the grades to help everyone have access to education regardless of location and status, only access to Internet being the main requirement :)
                        <br><br> 
                       This was my first hackathon win! Super proud of the concept and even though the tech stack wasn't the most efficient, we managed create a working prototype in less than 48 hours.
                       Would love to expand on this in the future maybe.
                        <br><br>
                        Technologies used: React, Python, JavaScript, Flask, SQLAlchemy.
                        <br><br>
                    </p>
                </Card>

                <Card name={"CampusWorks"} img={"collegeworks.jpeg"} url={"https://devpost.com/software/college-j7xsbk"}  on:sub={handleSub} bind:maybe={subp}>
                    <p slot="desc">
                        CollegeWorks is a web app that allows students to find nearby jobs and companies which they could apply to.
                        <br><br> 
                        It is built using React for the frontend, and Flask for API and basic backend.
                        <br><br>
                        Technologies used: Python, Flask, SQLite, React.
                        <br><br>
                    </p>
                </Card>

                

        </article>
        <Nav />
    </div>


<style>
    .close{
        right:0px;

    }
    .c2{
        right:65px;
    }
    .panel{
        top: 3vh;
        height: 97vh;
        min-width: 300px;
        left:3vw;
        width: 94vw;
        border-radius: 15px 15px 0px 0px;
    }

    h2{
        padding-left: calc(1vw + 10px);
        flex-direction: row;
    }



    a{
        text-decoration: underline
    }
    article{
        display: flex;
    justify-content: space-evenly;
    flex-wrap: wrap
    }
 p{
         padding:0px;
    margin-left:20px;
    margin-right:20px;
    font-size: 1.5em;
 }
</style>