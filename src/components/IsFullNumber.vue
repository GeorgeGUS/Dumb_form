<template>
  <div>
    <p class="text-center">Is this your real phone number? o_O</p>
    <button type="button" class="btn btn-success">yep! 😎</button>
    <button type="button" class="btn btn-warning">maybe... 🤔</button>
    <button type="button" class="btn btn-danger">lol, nope 😜</button>
  </div>
</template>

<script>
// по нажатию на среднюю кнопку перемешивать цифры в полях и задавать вопросы типа
// "And now?", "Maybe that one?". После пяти попыток сортировки выдать сообщение
// типа "You have exhausted all attempts. Your number will be deleted."
// При ответе "Нет" показывать по углам экрана картинки из мема "Oh you",
// где мужик укоряюще смотрит на своего пса =)
export default {
  name: "IsFullNumber"
};
</script>

<style>
.btn {
  font-size: 1.5em;
  margin: 0.2em;
  padding: 0.2em 0.5em;
  border-radius: 0.25em;
}

.text-center {
  text-align: center;
}
</style>
