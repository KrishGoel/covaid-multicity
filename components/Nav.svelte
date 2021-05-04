<style>
    nav {
        padding: 10px 0;
        position: sticky;
        top: 0;
        background-color: var(--light-dark-bg);
        box-shadow: 0 10px 20px -15px rgb(11, 3, 26);
    }

    nav .width-restriction {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    nav .width-restriction h1 {
        margin-right: 20px;
    }

    nav .width-restriction a {
        margin-right: 20px
    }

    nav .horizontal-scrollable {
        overflow: auto;
        white-space: nowrap;
        -webkit-overflow-scrolling: touch;
        -ms-overflow-style: -ms-autohiding-scrollbar;
    }
    nav .horizontal-scrollable a {
        display: inline-block;
        margin-right: 5px;
        color: var(--link-color);
        padding: 5px;
        box-shadow: inset 0 -2px 0 var(--link-color);
        transition: 0.2s;
    }
    nav .horizontal-scrollable a:hover {
        box-shadow: inset 0 -30px 0 var(--link-color);
        color: var(--dark-bg)
    }
</style>

<nav>
    <div class="width-restriction">
        <h1 style="margin-bottom: 0">CovAID</h1>
        <div class="horizontal-scrollable">
            <a href="/"><h5>Cities</h5></a>
            <a href="/volunteer"><h5>Volunteer</h5></a>
            <a href="/about"><h5>Partners</h5></a>
        </div>
    </div>
</nav>	
