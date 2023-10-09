<script setup>
import heic2any from 'heic2any';

const convertFile = async (event) => {
  const file = event.target.files[0];
  const fileName = file.name.replace('.heic', '.jpg');
  const lastModified = new Date().getTime();

  const blob = new Blob([file], { type: file.type });

  const converted = await heic2any({blob, toType: 'image/jpeg'});

  console.log(blobToFile(converted, fileName, lastModified));
}

const blobToFile = (blob, filename, lastModified) => {
  const fileParts = [blob];

  return new File(fileParts, filename, {lastModified});
}
</script>

<template>
  <input type="file" @input="convertFile">
</template>

<style scoped>
</style>
