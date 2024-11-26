<template>
  <div>
    <div class="toolbar">
      <button @click="execCommand('undo')" title="Назад по истории">
        <img src="../assets/Group 1.png" alt="" />
      </button>
      <button @click="execCommand('redo')" title="Вперёд по истории">
        <img src="../assets/Group 2.png" alt="" />
      </button>
      <button
        @click="execCommand('formatBlock', '<h1>')"
        title="Превратить в заголовок"
      >
        <img src="../assets/Group 3.png" />
      </button>
      <button
        @click="execCommand('formatBlock', '<p>')"
        title="Превратить в абзац"
      >
        <img src="../assets/Group 5.png" />
      </button>
      <button @click="insertImage()" title="Загрузить картинку">
        <img src="../assets/Group 4.png" />
      </button>
      <button class="copy" @click="copyHTML()" title="Скопировать HTML">
        Скопировать HTML
      </button>
    </div>

    <div class="paragraph" contenteditable="true" ref="editor" @input="onInput">
      <p>
        Таким образом консультация с широким активом представляет собой
        интересный эксперимент проверки позиций, занимаемых участниками в
        отношении поставленных задач. С другой стороны постоянное
        информационно-пропагандистское обеспечение нашей деятельности
        представляет собой интересный эксперимент проверки форм развития.
        Идейные соображения высшего порядка, а также укрепление и развитие
        структуры влечет за собой процесс внедрения и модернизации
        соответствующий условий активизации. Задача организации, в особенности
        же реализация намеченных плановых заданий играет важную роль в
        формировании дальнейших направлений развития. Повседневная практика
        показывает, что постоянное информационно-пропагандистское обеспечение
        нашей деятельности играет важную роль в формировании существенных
        финансовых и административных условий.
      </p>
      <h1>Смотрите какие обезьянки</h1>
      <img class="picture" src="../assets/image 1.jpg" alt="#" />

      <p>
        Таким образом консультация с широким активом представляет собой
        интересный эксперимент проверки позиций, занимаемых участниками в
        отношении поставленных задач. С другой стороны постоянное
        информационно-пропагандистское обеспечение нашей деятельности
        представляет собой интересный эксперимент проверки форм развития.
        Идейные соображения высшего порядка, а также укрепление и развитие
        структуры влечет за собой процесс внедрения и модернизации
        соответствующий условий активизации. Задача организации, в особенности
        же реализация намеченных плановых заданий играет важную роль в
        формировании дальнейших направлений развития. Повседневная практика
        показывает, что постоянное информационно-пропагандистское обеспечение
        нашей деятельности играет важную роль в формировании существенных
        финансовых и административных условий. <br />
        <br />
        Товарищи! новая модель организационной деятельности требуют от нас
        анализа направлений прогрессивного развития. Задача организации, в
        особенности же постоянный количественный рост и сфера нашей активности
        требуют от нас анализа позиций, занимаемых участниками в отношении
        поставленных задач. Задача организации, в особенности же реализация
        намеченных плановых заданий требуют от нас анализа системы обучения
        кадров, соответствует насущным потребностям.
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const editor = ref(null);

const execCommand = (command, value = null) => {
  document.execCommand(command, false, value);
};

const insertImage = () => {
  const url = prompt('Введите URL изображения:');
  if (url) {
    execCommand('insertImage', url);
  }
};

const copyHTML = () => {
  const html = editor.value.innerHTML;
  navigator.clipboard
    .writeText(html)
    .then(() => alert('текст скопирован в буфер обмена!'))
    .catch(() => alert('Ошибка'));
};

const onInput = () => {
  console.log(editor.value.innerHTML);
};
</script>

<style>
.toolbar {
  display: flex;
  gap: 10px;
  margin-bottom: 15px;
}

.toolbar button {
  color: #639eff;
  background-color: #282c34;

  border: none;
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;
}

.toolbar button:hover {
  background-color: #555a62;
}
.picture {
  width: 739px;
  height: 308px;
}
.paragraph {
  padding: 10px;
  background-color: #282c34;
  color: #eaeaea;
  font-size: 15px;
  font-weight: 400;
  line-height: 23px;
  text-align: left;
}

.paragraph:focus {
  outline: none;
}
</style>
