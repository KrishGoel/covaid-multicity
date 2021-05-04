<style>
    footer {
        padding: 15px 0;
        position: sticky;
        top: 0;
        background-color: var(--light-dark-bg);
        box-shadow: 0 10px 20px -15px rgb(11, 3, 26);
    }

    footer .width-restriction {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    footer .width-restriction h3 {
        margin-right: 20px;
    }

    footer .width-restriction a {
        margin-right: 20px
    }

    footer .horizontal-scrollable {
        overflow: auto;
        white-space: nowrap;
        -webkit-overflow-scrolling: touch;
    }
    footer .horizontal-scrollable a {
        display: inline-block;
        margin-right: 5px;
        color: var(--link-color);
        padding: 5px;
        box-shadow: inset 0 -2px 0 var(--link-color);
        transition: 0.2s;
    }
    footer .horizontal-scrollable a:hover {
        box-shadow: inset 0 -30px 0 var(--link-color);
        color: var(--dark-bg)
    }
</style>

<footer>
    <div class="width-restriction">
        <a href="https://github/KrishSkywalker/covaid" class="mono"><h3>-v2.0</h3></a>
        <div class="horizontal-scrollable">
            <a href="/about"><h5>Verification</h5></a>
            <a href="/about"><h5>Partners</h5></a>
            <a href="/about"><h5>About Us</h5></a>
            <a href="/about"><h5>Twitter</h5></a>
            <a href="/about"><h5>Instagram</h5></a>
        </div>
    </div>
</footer>	
