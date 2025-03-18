<template>
  <q-page class="homepage">
    <div class="content">
      <h1 class="text-bold">Smooch Utils</h1>
      <p>
        "Smooch Utils" is an application designed to simplify integration with the Smooch API. It offers a collection of useful tools for developers, helping to streamline common tasks and improve productivity.
      </p>
      <h2>Features:</h2>
      <ul>
        <li>JWT token generation for authentication with the Smooch API.</li>
        <li>Tools for validation and manipulation of Smooch-related data.</li>
        <li>Intuitive and user-friendly interface built with the Quasar Framework.</li>
      </ul>
      <h2>Technologies:</h2>
      <ul>
        <li>Vue 3 with Composition API.</li>
        <li>Quasar Framework for UI components.</li>
        <li>Modern libraries for data manipulation and authentication.</li>
      </ul>
      <h2>How to use:</h2>
      <ol>
        <li>Select the desired tool from the main menu.</li>
        <li>Follow the specific instructions for each feature.</li>
        <li>Use the generated results to integrate or test your application.</li>
      </ol>
      <h2>Note:</h2>
      <p>
        "Smooch Utils" is designed for developers and technical teams. Make sure to provide valid inputs to achieve the best results.
      </p>
    </div>
    <footer class="footer">
      <p>Made with ❤️ by Lourenço Carlos (Enzadaz)</p>
      <p>
        <a href="https://github.com/reincedaniel/smooch-utils" target="_blank">GitHub</a> |
        <a href="https://www.linkedin.com/in/louren%C3%A7o-carlos-25a162146/" target="_blank">LinkedIn</a>
      </p>
    </footer>
  </q-page>
</template>

<style scoped>
.homepage {
  background-color: #ffffff;
  color: #333333;
  padding: 20px;
  font-family: Arial, sans-serif;
}

.content h1 {
  color: #03363D;
  font-size: 24px;
}

.content h2 {
  color: #555555;
  font-size: 18px;

}

.content p,
.content ul,
.content ol {
  color: #666666;
  font-size: 16px;
  line-height: 1.6;
}

.content ul,
.content ol {
  padding-left: 20px;
}

.footer {
  margin-top: 20px;
  text-align: center;
  color: #777777;
  font-size: 12px;
}

.footer a {
  color: #007bff;
  text-decoration: none;
}

.footer a:hover {
  text-decoration: underline;
}
</style>
