**Read in other languages: [English](README.en.md), [Українська](README.md).**

# Підготовка проекту

1. Встановлено LTS-версію Node.js.
2. Цей проект було створено за допомогою
   [Create React App](https://github.com/facebook/create-react-app). Для
   ознайомлення та налаштування додаткових можливостей
   [зверніться до документації](https://facebook.github.io/create-react-app/docs/getting-started).
3. Встановлено базові залежності проекту командою `npm install`.
4. Запуск режиму розробки виконується командою `npm start`.
5. Сторінка в браузері за адресою
   [http://localhost:3000](http://localhost:3000).

# Критерії приймання

- Створено репозиторій `goit-react-hw-02-phonebook`.
- При здачі домашньої роботи є два посилання: на вихідні файли та робочі
  сторінки кожного завдання на `GitHub Pages`.
- Під час запуску коду завдання в консолі відсутні помилки та попередження.
- Для кожного компонента є окремий файл у папці `src/components`.
- Для компонентів описані `propTypes`.
- Все, що компонент очікує у вигляді пропсів, передається йому під час виклику.
  JS-код чистий і зрозумілий, використовується `Prettier`.
- Стилізація виконана `CSS-модулями` або `Styled Components`.

## 2 - Книга контактів

Напиши застосунок зберігання контактів телефонної книги.

### Крок 1

Застосунок повинен складатися з форми і списку контактів. На поточному кроці
реалізуй додавання імені контакту та відображення списку контактів. Застосунок
не повинен зберігати контакти між різними сесіями (оновлення сторінки).

Використовуйте цю розмітку інпуту з вбудованою валідацією для імені контакту.

```html
<input
  type="text"
  name="name"
  pattern="^[a-zA-Zа-яА-Я]+(([' -][a-zA-Zа-яА-Я ])?[a-zA-Zа-яА-Я]*)*$"
  title="Name may contain only letters, apostrophe, dash and spaces. For example Adrian, Jacob Mercer, Charles de Batz de Castelmore d'Artagnan"
  required
/>
```

Стан, що зберігається в батьківському компоненті `<App>`, обов'язково повинен
бути наступного вигляду, додавати нові властивості не можна.

```js
state = { contacts: [], name: '' };
```

Кожен контакт повинен бути об'єктом з властивостями `name` та `id`. Для
генерації ідентифікаторів використовуй будь-який відповідний пакет, наприклад
[nanoid](https://www.npmjs.com/package/nanoid). Після завершення цього кроку,
застосунок повинен виглядати приблизно так.

<Image
  src="./assets/step-1.png"
  alt="component preview"
  maxWidth={960}
/>

### Крок 2

Розшир функціонал застосунку, дозволивши користувачам додавати номери телефонів.
Для цього додай `<input type="tel">` у форму і властивість для зберігання його
значення в стані.

```js
state = {
  contacts: [],
  name: '',
  number: '',
};
```

Використовуй цю розмітку інпуту з вбудованою валідацією для номеру контакту.

```html
<input
  type="tel"
  name="number"
  pattern="\+?\d{1,4}?[-.\s]?\(?\d{1,3}?\)?[-.\s]?\d{1,4}[-.\s]?\d{1,4}[-.\s]?\d{1,9}"
  title="Phone number must be digits and can contain spaces, dashes, parentheses and can start with +"
  required
/>
```

Після завершення цього кроку, застосунок повинен виглядати приблизно так.

<Image
  src="./assets/step-2.png"
  alt="component preview"
  maxWidth={960}
/>

### Крок 3

Додай поле пошуку, яке можна використовувати для фільтрації списку контактів за
ім'ям.

Поле пошуку – це інпут без форми, значення якого записується у стан
(контрольований елемент). Логіка фільтрації повинна бути нечутливою до регістру.

```js
state = {
  contacts: [],
  filter: '',
  name: '',
  number: '',
};
```

<Image
  src="./assets/step-3.gif"
  alt="component preview"
  maxWidth={960}
/>

Коли ми працюємо над новим функціоналом, буває зручно жорстко закодувати деякі
дані у стан. Це позбавить необхідності вручну вводити дані в інтерфейсі для
тестування роботи нового функціоналу. Наприклад, можна використовувати такий
початковий стан.

```js
state = {
  contacts: [
    { id: 'id-1', name: 'Rosie Simpson', number: '459-12-56' },
    { id: 'id-2', name: 'Hermione Kline', number: '443-89-12' },
    { id: 'id-3', name: 'Eden Clements', number: '645-17-79' },
    { id: 'id-4', name: 'Annie Copeland', number: '227-91-26' },
  ],
  filter: '',
  name: '',
  number: '',
};
```

### Крок 4

Якщо твій застосунок реалізований в одному компоненті `<App>`, виконай
рефакторинг, виділивши відповідні частини в окремі компоненти. У стані
кореневого компонента `<App>` залишаться тільки властивості `contacts` і
`filter`.

```js
state = {
  contacts: [],
  filter: '',
};
```

Достатньо виділити чотири компоненти: форма додавання контактів, список
контактів, елемент списку контактів та фільтр пошуку.

Після рефакторингу кореневий компонент застосунку виглядатиме так.

```html
<div>
  <h1>Phonebook</h1>
  <ContactForm ... />

  <h2>Contacts</h2>
  <Filter ... />
  <ContactList ... />
</div>
```

### Крок 5

Заборони користувачеві можливість додавати контакти, імена яких вже присутні у
телефонній книзі. При спробі виконати таку дію виведи `alert` із попередженням.

<Image
  src="./assets/step-5.png"
  alt="component preview"
  maxWidth={960}
/>

### Крок 6

Розшир функціонал застосунку, дозволивши користувачеві видаляти раніше збережені
контакти.

<Image
  src="./assets/step-6.gif"
  alt="component preview"
  maxWidth={960}
/>
