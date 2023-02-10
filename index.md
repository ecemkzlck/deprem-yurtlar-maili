{% include_relative mail.md %}


<textarea style="height: 0px; max-height: 0px; width: 0px; max-width: 0px; opacity: 0" id="textarea">
{% include_relative mail.md %}
</textarea>

<button id="button" data-clipboard-action="copy" data-clipboard-target="#textarea" data-tippy-content="Copied, opening mail client">
    Mail Gönder
</button>

<script src="https://unpkg.com/@popperjs/core@2"></script>
<script src="https://unpkg.com/tippy.js@6"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/clipboard.js/2.0.4/clipboard.min.js"></script>
<script>
document.addEventListener("DOMContentLoaded", function() {
    new ClipboardJS('#button');

    tippy('#button', {
        trigger: 'click',
    });

    document.getElementById('button').addEventListener('click', function() {
        let address_data = `{% include_relative addresses.md %}`;
        address_data = address_data.replace(/\n/g, ',');
        let subject_data = `{% include_relative subject.md %}`;
        subject_data = subject_data.replace(/ /g, '%20');
        let body_data = `{% include_relative mail.md %}`;
        body_data = body_data.replace(/\n/g, '%0D%0A');

        console.log(`mailto:${address_data}?subject=${subject_data}&body=${body_data}`);
        setTimeout(function() {
            window.location.href = `mailto:${address_data}?subject=${subject_data}&body=${body_data}`;
        }, 550);
    });
});
</script>
