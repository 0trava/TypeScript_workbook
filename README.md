# TypeScript_workbook

### Створення нового проєкту
my-app — це назва вашого нового проєкту. Ви можете обрати будь-яке ім'я, яке вам подобається. Прапорець --template typescript вказує create-react-app використовувати шаблон TypeScript для нового проєкту.
Ця команда створить новий каталог з назвою вашого проєкту, встановить усі необхідні залежності та створить стартовий проєкт React із TypeScript.
~~~
npx create-react-app my-app --template typescript
~~~

### Міграція проєкту на TypeScript
Якщо ви вже маєте проєкт і хочете додати TypeScript, виконайте такі кроки:
Це встановить TypeScript у ваш проєкт, а також типи для бібліотек React та ReactDOM, які надають автозаповнення та перевірку типів для API цих бібліотек.
~~~
npm install --save typescript @types/react @types/react-dom
~~~

Додайте конфігурацію TypeScript:
У кореневому каталозі проєкту створіть файл tsconfig.json. Цей файл містить конфігурацію TypeScript для вашого проєкту.
~~~
{
  "compilerOptions": {
    "target": "es5",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "noFallthroughCasesInSwitch": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx"
  },
  "include": ["src", "@types"]
}
~~~

Створіть у кореневому каталозі проєкту папку @types і додайте файл custom.d.ts. Всередині цього файлу опишіть наступний код:
Це потрібно для того, щоб TypeScript правильно обробляв файли з розширеннями .svg та .png. Без цього імпорти виду import logo from "./logo.svg"; викликатимуть помилку.
~~~
declare module "*.svg" {
  const content: any;
  export default content;
}

declare module "*.png" {
  const content: any;
  export default content;
}
~~~

Перейменуйте файли:
Файли TypeScript мають розширення .ts для файлів без JSX та .tsx для файлів з JSX. Вам потрібно перейменувати всі файли .js і .jsx на .ts і .tsx відповідно.
Ви можете це робити поступово, тому що в конфігурації TypeScript ви вказали "allowJs": true, що дозволяє проєкту змішувати файли TypeScript та JavaScript.

### Використання сторонніх бібліотек
Іноді ви можете зіткнутися з бібліотекою, що не підтримує TypeScript з коробки. У цьому випадку вам потрібно встановити окремі визначення типів для цієї бібліотеки.
DefinitelyTyped — це репозиторій на GitHub, у якому спільнота TypeScript підтримує визначення типів для тисяч JavaScript-бібліотек.
~~~
yarn add -D @types/имя_библиотеки
# или
npm install --save-dev @types/имя_библиотеки
~~~
Наприклад, для бібліотеки react-router-dom команда виглядатиме так:
~~~
yarn add -D @types/react-router-dom
# или
npm install --save-dev @types/react-router-dom
~~~


