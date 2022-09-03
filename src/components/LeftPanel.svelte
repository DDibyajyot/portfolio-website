<script>
	import { slide } from 'svelte/transition';
    import { quintInOut } from 'svelte/easing';
    import Nav from './Nav.svelte'
    
    	function swipeLeft(node, { duration }) {
		return {
			duration,
			css: t => {
				const eased = quintInOut(t);
				return `
                    transform: translate3d(-${(1-eased)*100}%,0,0);
                    `
			}
		};
	}
</script>

    <div transition:swipeLeft={{duration: 800 }}  class="panel">
        <a class="close" href="#home"> 
            <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.25" stroke-linecap="round" stroke-linejoin="round" class="feather feather-x"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg>
        </a>
        <h2>About</h2>
        <article >
        <div  class="pp"></div>
            <p>Hey there!</p>
            <p> I'm Deepam Dibyajyot. I am a second year student at the University of Waterloo and I am majoring in Computer Science! I am currently looking for internships for Winter 2022 in
            SWE, Full-Stack, ML/AI and Data Analyst roles.</p>
            <p> I love space, books, anime, gaming and trying out new stuff! Most of the times you'd find me having a deep philosophical conversation with someone or just simply goofing around :> </p>
            <p>You could take a look at all my projects and internship experiences <a href="#projects">here</a>, and feel free to reach out to me <a href="#contact"> here</a>! </p>
            <p>My goal is to be able to keep expanding the thresholds of what is possible in the future, and to be able to do so with the help of the people I meet and the technologies I work with.</p> 
            <!-- <p>
            My most recent large project  </p> -->
        </article>
        <Nav />
    </div>



<style>
    .close{
        right:0px;

    }
    .pp{
        height: 200px;
        width: 200px;
        border-radius: 50%;
  margin-bottom: 10px;
margin-top:20px;
    margin-left: auto;
    margin-right: auto;

        background-image: url("/deep.jpg");
        background-position: center;
        background-size: cover;
    }
    .panel{
        top: 3vh;
        height: 94vh;
        min-width: 350px;
        width: 60vw;
        border-radius: 0px 15px 15px 0px;
    }
    h2{
        
        padding-left: calc(1vw + 10px);

        flex-direction: row;

    }
 
    a{
        text-decoration: underline
    }
    @media only screen and (max-width: 1000px) {
        .panel{
                 width: 75vw;
        }
    }
    @media only screen and (max-width: 750px) {
        .panel{
                 width: 85vw;
        }

    }
</style>