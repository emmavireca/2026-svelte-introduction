<script>
    let size = $state(50)
    let color = $state ("aff13e00")
    
</script>

<h3>Canvas Square</h3>

<article>
     <!-- //spazio vuoto dove dsegni ogni pixel// -->
    <canvas width ="100" height="100"></canvas> 
    <nav>
       <label>
        Size: <input type="range">
       </label>

       <label>
        Color: <input type="color">
       </label>
    </nav>
</article>

<style>
 article {
    display: flex;
    gap: 1em;
    align-items: end;
 }

 canvas {
    border: solid 1px black;
 }
 
 nav {
    display: flex;
    gap: 1em;

 }
</style>