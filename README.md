<!-- 🚧⛔ -->
<!-- ⚠️ -->
<!-- 🚩 -->
<!-- 🏁  -->
<!-- 🏁❗  -->
<!-- ✔️  -->
<!--  ✅    -->
<!--  ▶️    -->

### **❓ Questão: editar múltiplos registros marcados como checked de uma tabela em um base de dados websql**
    @Descrição Para editar múltiplos registros marcados como "checked" em uma tabela em uma base de dados WebSQL,
    você precisará escrever uma consulta SQL que atualize os dados na tabela.
    Aqui está um exemplo geral de como você poderia fazê-lo:

    ✔️ 1. Recupere os IDs dos registros marcados como "checked".
    ✔️ 2. Construa uma consulta SQL que atualize a tabela, utilizando os IDs recuperados como parte da cláusula "WHERE".
    ✔️ 3. Execute a consulta SQL usando a função "executeSql" da interface WebSQL.

#### ***✍️Exemplo de código***
``` JS
var db = window.openDatabase("database", "1.0", "database", 2 * 1024 * 1024);
var checkedIds = [1, 2, 3]; // IDs dos registros marcados como "checked"
var updateSql = "UPDATE table SET column1 = 'value1', column2 = 'value2' WHERE id IN (" + checkedIds.join(",") + ")";
db.transaction(function (tx) {
   tx.executeSql(updateSql, [], function (tx, result) {
     console.log("Success: " + result.rowsAffected + " row(s) updated.");
   }, function (tx, error) {
     console.log("Error: " + error.message);
  });
});
```

### **🏁❗ implemente ao código verificar todos os input marcados como checked que pertecen a class x**

    @Descrição Aqui, usamos a seleção querySelectorAll para recuperar todos os inputs com o atributo type igual a checkbox e o atributo checked definido, que pertencem à classe "x".
    Em seguida, adicionamos o valor de cada input recuperado a um array de IDs.
    Finalmente, construímos a consulta SQL e executamos-na da mesma maneira que no exemplo anterior.


#### ***✍️Exemplo de código***

``` JS
var checkedInputs = document.querySelectorAll(".x input[type='checkbox']:checked");
var checkedIds = [];
for (var i = 0; i < checkedInputs.length; i++) {
  checkedIds.push(checkedInputs[i].value);
}

var db = window.openDatabase("database", "1.0", "database", 2 * 1024 * 1024);
var updateSql = "UPDATE table SET column1 = 'value1', column2 = 'value2' WHERE id IN (" + checkedIds.join(",") + ")";
db.transaction(function (tx) {
  tx.executeSql(updateSql, [], function (tx, result) {
    console.log("Success: " + result.rowsAffected + " row(s) updated.");
  }, function (tx, error) {
    console.log("Error: " + error.message);
  });
});
```

### **🏁❗ implementar uma estrutura try-catch ao código**

    @Descrição Aqui, adicionamos uma estrutura try-catch em volta do código que executa a transação na base de dados. Caso ocorra algum erro, ele será capturado e tratado dentro do bloco catch. Usamos console.error para exibir uma mensagem de erro e, em seguida, implementamos a nossa tratativa de erro personalizada, como exibir uma mensagem de erro ao usuário, por exemplo.

#### ***✍️Exemplo de código***


``` JS
var checkedInputs = document.querySelectorAll(".x input[type='checkbox']:checked");
var checkedIds = [];
for (var i = 0; i < checkedInputs.length; i++) {
  checkedIds.push(checkedInputs[i].value);
}

var db = window.openDatabase("database", "1.0", "database", 2 * 1024 * 1024);
var updateSql = "UPDATE table SET column1 = 'value1', column2 = 'value2' WHERE id IN (" + checkedIds.join(",") + ")";
try {
  db.transaction(function (tx) {
    tx.executeSql(updateSql, [], function (tx, result) {
      console.log("Success: " + result.rowsAffected + " row(s) updated.");
    });
  });
} catch (error) {
  console.error("Error updating data: " + error.message);
  // Implementar aqui a sua tratativa de erro, por exemplo, exibindo uma mensagem de erro ao usuário
}

```

### **🏁❗ implementar uma Promise ao código**

    @DescriçãoAqui, criamos uma função updateData que retorna uma Promise. Dentro da função, adicionamos o código que executa a transação na base de dados. Se a transação for bem-sucedida, chamamos o resolve e passamos o resultado da operação. Caso contrário, chamamos o reject e passamos o erro. Em seguida, usamos o método then para registrar a ação a ser executada em caso de sucesso e o método catch para registrar a ação a ser executada em caso de erro.

#### ***✍️Exemplo de código***

``` JS
var checkedInputs = document.querySelectorAll(".x input[type='checkbox']:checked");
var checkedIds = [];
for (var i = 0; i < checkedInputs.length; i++) {
  checkedIds.push(checkedInputs[i].value);
}

var db = window.openDatabase("database", "1.0", "database", 2 * 1024 * 1024);
var updateSql = "UPDATE table SET column1 = 'value1', column2 = 'value2' WHERE id IN (" + checkedIds.join(",") + ")";

function updateData() {
  return new Promise(function (resolve, reject) {
    db.transaction(function (tx) {
      tx.executeSql(updateSql, [], function (tx, result) {
        console.log("Success: " + result.rowsAffected + " row(s) updated.");
        resolve(result);
      }, function (tx, error) {
        console.error("Error updating data: " + error.message);
        reject(error);
      });
    });
  });
}

updateData()
  .then(function (result) {
    // Código a ser executado em caso de sucesso
  })
  .catch(function (error) {
    // Implementar aqui a sua tratativa de erro, por exemplo, exibindo uma mensagem de erro ao usuário
  });

```

### **🏁❗ implementar Async/Await ao código**

    Aqui, declaramos a função updateData como async e o código que chama a função está dentro de uma função auto-executável. Usamos o await para esperar a conclusão da Promise retornada pela função updateData e armazenamos o resultado na variável result. Em seguida, usamos um bloco try...catch para lidar com possíveis erros que possam ocorrer durante a operação.


#### ***✍️Exemplo de código***

``` JS
var checkedInputs = document.querySelectorAll(".x input[type='checkbox']:checked");
var checkedIds = [];
for (var i = 0; i < checkedInputs.length; i++) {
  checkedIds.push(checkedInputs[i].value);
}

var db = window.openDatabase("database", "1.0", "database", 2 * 1024 * 1024);
var updateSql = "UPDATE table SET column1 = 'value1', column2 = 'value2' WHERE id IN (" + checkedIds.join(",") + ")";

async function updateData() {
  return new Promise(function (resolve, reject) {
    db.transaction(function (tx) {
      tx.executeSql(updateSql, [], function (tx, result) {
        console.log("Success: " + result.rowsAffected + " row(s) updated.");
        resolve(result);
      }, function (tx, error) {
        console.error("Error updating data: " + error.message);
        reject(error);
      });
    });
  });
}

(async function () {
  try {
    const result = await updateData();
    // Código a ser executado em caso de sucesso
  } catch (error) {
    // Implementar aqui a sua tratativa de erro, por exemplo, exibindo uma mensagem de erro ao usuário
  }
})();

```


### **👉👍 Comentários Finais**

``` JS

// Selecione todos os inputs marcados como checked que pertencem à classe "x"
var checkedInputs = document.querySelectorAll(".x input[type='checkbox']:checked");

// Armazene o ID dos inputs selecionados em um array
var checkedIds = [];
for (var i = 0; i < checkedInputs.length; i++) {
  checkedIds.push(checkedInputs[i].value);
}

// Abra a base de dados WebSQL
var db = window.openDatabase("database", "1.0", "database", 2 * 1024 * 1024);

// Crie a string SQL para atualizar as linhas selecionadas
var updateSql = "UPDATE table SET column1 = 'value1', column2 = 'value2' WHERE id IN (" + checkedIds.join(",") + ")";

// Declare a função async para atualizar os dados
async function updateData() {
  // Retorne uma nova Promise
  return new Promise(function (resolve, reject) {
    // Execute a transação no banco de dados
    db.transaction(function (tx) {
      // Execute a consulta SQL
      tx.executeSql(updateSql, [], function (tx, result) {
        // Log do resultado da atualização bem-sucedida
        console.log("Success: " + result.rowsAffected + " row(s) updated.");
        // Resolva a Promise com o resultado
        resolve(result);
      }, function (tx, error) {
        // Log de erro ao atualizar os dados
        console.error("Error updating data: " + error.message);
        // Rejeite a Promise com o erro
        reject(error);
      });
    });
  });
}

// Chamada auto-executável para atualizar os dados
(async function () {
  // Use um bloco try...catch para lidar com possíveis erros
  try {
    // Aguarde a Promise ser resolvida e armazene o resultado
    const result = await updateData();
    // Código a ser executado em caso de sucesso
  } catch (error) {
    // Implementar aqui a sua tratativa de erro, por exemplo, exibindo uma mensagem de erro ao usuário
  }
})();


```