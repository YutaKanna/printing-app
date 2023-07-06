<template>
    <div>
      <button @click="printCheck">小切手を印刷</button>
    </div>
  </template>
  
  <script>
  import html2pdf from 'html2pdf.js';

  export default {
    name: 'CheckPrinter',
    methods: {
      printCheck() {
        const content = `
          <div style="width: 8.5in; height: 11in; border: 1px solid black; padding: 1in;">
            <h1>小切手印刷アプリ</h1>
            <h2>小切手情報</h2>
            <p>受取人: 山田太郎</p>
            <p>金額: 100,000円</p>
            <p>日付: 2023年7月6日</p>
          </div>
        `;
  
        const element = document.createElement('div');
        element.innerHTML = content;
  
        html2pdf().from(element).save();
      },
    },
  };
  </script>
  