<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>Homework</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.0.0/animate.min.css">
  <style>
    .message {
      width: 150px;
      padding: 20px;
      background: lightgoldenrodyellow;
      border: 1px solid orange;
      visibility: hidden;
    }

    .error {
      border: 0.3rem solid red;
    }
  </style>
</head>

<body>
  <!--
Обязательное задание.
Выполнить все задачи в теге script. Комментарии, в которых написаны задачи, не
стирать, код с решением задачи пишем под комментарием.
-->

  <input id="from" type="text">
  В инпуте написано: <span></span>

  <br>

  <button class="messageBtn">Показать блок</button>
  <div class="message">
    Привет :)
  </div>

  <br>

  <form>
    <label>
      Первый инпут:
      <input class="form-control" type="text">
    </label>
    <br>
    <br>
    <label>
      Второй инпут:
      <select class="form-control">
        <option value=""></option>
        <option value="1">Один</option>
        <option value="2">Два</option>
      </select>
    </label>
    <br>
    <br>
    <button>Отправить</button>
  </form>

  <script>
    "use strict";

    /*
    1. При изменении значения в input с id="from", значение содержащееся в нем
    должно моментально отображаться в span. То есть при печати в input'е тег span
    также должен меняться.
    */
    const spanEl = document.querySelector('span');
    document.querySelector('input').addEventListener('input', e => {
      spanEl.textContent = e.target.value;
    });

    /*
    2. При клике на кнопку с классом messageBtn необходимо элементу с классом
    message:
    1) добавить два класса: animate__animated и animate__fadeInLeftBig
    2) поставить данному элементу стиль visibility в значение 'visible'.
     */
    const message = document.querySelector('.message');
    document.querySelector('button').addEventListener('click', () => {
      message.style.visibility = 'visible';
      message.classList.add('animate__animated', 'animate__fadeInLeftBig');
    });

    /*
    3. Необходимо при отправке формы проверить, заполнены ли все поля в этой
    форме. Если какое-либо поле не заполнено, форма не должна отправляться, также
    должны быть подсвечены незаполненные поля (необходимо поставить класс error
    незаполненным полям).
    Как только пользователь начинает заполнять какое-либо поле, необходимо,
    при вводе в данное поле, произвести проверку:
    Если поле пустое, необходимо данное поле подсветить (поставить класс error
    данному полю).
    Если поле было чем-либо заполнено, подсветку (класс error) необходимо убрать.
     */
    const formEl = document.querySelector('form');
    const formControlEls = formEl.querySelectorAll('input, select');
    formEl.addEventListener('submit', event => {
      formControlEls.forEach(formControlEl => {
        if (formControlEl.value === '') {
          formControlEl.classList.add('error');
          event.preventDefault();
        }
      });
    });

    formEl.addEventListener('input', event => {
      if (!event.target.classList.contains('form-control')) {
        return;
      }
      event.target.value === ''
        ? event.target.classList.add('error')
        : event.target.classList.remove('error');
    });

  </script>
</body>

</html>
