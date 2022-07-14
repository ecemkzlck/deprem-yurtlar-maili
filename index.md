{% include_relative mail.md %}


<textarea style="height: 0px; max-height: 0px; width: 0px; max-width: 0px; opacity: 0" id="textarea">
{% include_relative mail.md %}
</textarea>

<button id="button" data-clipboard-action="copy" data-clipboard-target="#textarea" data-tippy-content="Kopyalandı. Mail açılıyor">
    Metni Kopyala ve Mail'e Devam Et
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
        setTimeout(function() {
            window.location.href = `mailto:{% include_relative addresses.md %}?subject={% include_relative subject.md %}`;
        }, 550);
    });
});
</script>
