<template>
  <div class="writing-page">
    <div class="writing-block" @keyup.space="runCommand" contenteditable="true">
      <div>
        <br>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "WritingPage",
  methods: {
    runCommand() {
      var usingContentBlock = document.getSelection().anchorNode;
      var content = usingContentBlock.textContent;

      if(content.startsWith("-")) {
        document.execCommand("insertUnorderedList", false, "");
        document.getSelection().anchorNode.textContent = usingContentBlock.textContent.slice(1);
      }

      if(content.startsWith("1.")) {
        document.execCommand("insertOrderedList", false, "");
        document.getSelection().anchorNode.textContent = usingContentBlock.textContent.slice(1);
      }
    }
  }
}
</script>
