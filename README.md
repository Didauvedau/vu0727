# vu0727
di chuyển modal:
<script>
    var state = {
        isDragging: false,
        xDiff: 100,
        yDiff: 100,
        x: 0,
        y: 0,
    };

    function afterClick() {

        var modal = document.getElementById("modal-x");

        renderWindow(modal, state);

        var modalHeader = document.getElementById("modal-header");

        modalHeader.addEventListener("mousedown", onMouseDown);

        document.addEventListener("mousemove", onMouseMove);

        document.addEventListener("mouseup", onMouseUp);
    }

    function renderWindow(w, myState) {
        w.style.transform = "translate(" + myState.x + "px, " + myState.y + "px)";
    }

    function clampX(n) {
        return Math.min(Math.max(n, -500), 500);
    }

    function clampY(n) {
        return Math.min(Math.max(n, -500), 500);
    }

    function onMouseMove(e) {
        if (state.isDragging) {
            state.x = clampX(e.pageX - state.xDiff);
            state.y = clampY(e.pageY - state.yDiff);
        }

        // Update window position
        var modal = document.getElementById("modal-x");

        renderWindow(modal, state);
    }

    function onMouseDown(e) {
        state.isDragging = true;
        state.xDiff = e.pageX - state.x;
        state.yDiff = e.pageY - state.y;
    }

    function onMouseUp() {
        state.isDragging = false;
    }
</script>
