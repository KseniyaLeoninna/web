---
layout: page
title: Контакты
permalink: /contact
---

Свяжитесь с нами удобным способом — ответим в течение рабочего дня.

## Написать нам

**Email:** [info@amdev.ru](mailto:info@amdev.ru)

**Телефон:** [+7 (999) 000-00-00](tel:+79990000000)

## Оставить заявку

<form id="contact-form" name="contact" method="POST" data-netlify="true" class="mt-6 space-y-4 max-w-lg">
  <input type="hidden" name="form-name" value="contact" />
  <div class="form-field">
    <label class="block text-sm text-text-dim mb-1" for="name">Ваше имя</label>
    <input type="text" id="name" name="name" required class="w-full border border-border bg-surface px-3 py-2 text-text" />
    <p class="form-error">Пожалуйста, введите имя</p>
  </div>
  <div class="form-field">
    <label class="block text-sm text-text-dim mb-1" for="email">Email</label>
    <input type="email" id="email" name="email" required class="w-full border border-border bg-surface px-3 py-2 text-text" />
    <p class="form-error">Введите корректный email</p>
  </div>
  <div class="form-field">
    <label class="block text-sm text-text-dim mb-1" for="message">Сообщение</label>
    <textarea id="message" name="message" rows="4" required class="w-full border border-border bg-surface px-3 py-2 text-text"></textarea>
    <p class="form-error">Напишите сообщение</p>
  </div>
  <button type="submit" class="border border-accent text-accent px-5 py-2 text-sm hover:bg-accent hover:text-accent-text">Отправить</button>
</form>

<script>
  document.addEventListener("DOMContentLoaded", function () {
    var form = document.getElementById("contact-form");
    if (!form) return;

    form.addEventListener("submit", function (e) {
      e.preventDefault();
      var valid = true;
      var fields = form.querySelectorAll(".form-field");
      fields.forEach(function (field) {
        var input = field.querySelector("input, textarea");
        var value = input.value.trim();
        var fieldValid = true;
        if (input.type === "email") {
          fieldValid = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value);
        } else {
          fieldValid = value.length > 0;
        }
        if (!fieldValid) { field.classList.add("error"); valid = false; }
        else { field.classList.remove("error"); }
      });

      if (valid) {
        showToast("Спасибо! Мы свяжемся с вами.", "success");
        form.reset();
      } else {
        showToast("Проверьте поля формы.", "error");
      }
    });

    // Убираем ошибку при вводе
    form.querySelectorAll("input, textarea").forEach(function (input) {
      input.addEventListener("input", function () {
        input.closest(".form-field").classList.remove("error");
      });
    });
  });
</script>

## Реквизиты

**Amdev** — настройка и внедрение CRM-систем.