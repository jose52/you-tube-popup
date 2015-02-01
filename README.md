# you-tube-popup
Script to pop up you tube videos
<style>
.fancybox-nav {
    width: 60px;
}
.fancybox-nav span {
    visibility: visible;
}
.fancybox-next {
    right: -60px;
}
.fancybox-prev {
    left: -60px;
}
</style>
<script type="text/javascript">
// Fires whenever a player has finished loading
function onPlayerReady(event) {
        event.target.playVideo();
    }
    // Fires when the player's state changes.
function onPlayerStateChange(event) {
        // Go to the next video after the current one is finished playing
        if (event.data === 0) {
            $.fancybox.next();
        }
    }
    // The API will call this function when the page has finished downloading the JavaScript for the player API
function onYouTubePlayerAPIReady() {
    // Initialise the fancyBox after the DOM is loaded
    $(document).ready(function() {
        $(".fancybox")
            .attr('rel', 'gallery')
            .fancybox({
                openEffect: 'none',
                closeEffect: 'none',
                nextEffect: 'none',
                prevEffect: 'none',
                padding: 0,
                margin: 50,
                beforeShow: function() {
                    // Find the iframe ID
                    var id = $.fancybox.inner.find('iframe').attr('id');
                    // Create video player object and add event listeners
                    var player = new YT.Player(id, {
                        events: {
                            'onReady': onPlayerReady,
                            'onStateChange': onPlayerStateChange
                        }
                    });
                }
            });
    });
}
</script>
<script type="text/javascript">
function showPopup(url) {
    newwindow = window.open(url, 'name', 'height=315,width=560,top=200,left=800,resizable');
    if (window.focus) {
        newwindow.focus()
    }
}
</script>
<!-- This loads the YouTube IFrame Player API code -->
<script src="http://www.youtube.com/player_api"></script>
<div style="width:200px;">
    <h2>//Title//</h2>
    <a class="fancybox fancybox.iframe" href="http://www.youtube.com/embed////End of Video Embed Code//?enablejsapi=1&wmode=opaque" target="blank" onClick='showPopup(this.href);return(false);'><img src="//Thumb//" />
    </a>
</div>
