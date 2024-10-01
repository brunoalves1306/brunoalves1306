- 👋 Hi, const express = require('express');
const router = express.Router();
const alunoController = require('./controllers/alunoController');

// Rota para listar alunos
router.get('/alunos', alunoController.listarAlunos);

// Rota para exibir o formulário de cadastro
router.get('/alunos/cadastrar', alunoController.formCadastro);

// Rota para criar um novo aluno
router.post('/alunos', alunoController.criarAluno);

module.exports = router;
const Aluno = require('../models/Aluno'); // Supondo que você tenha um modelo Aluno

exports.listarAlunos = async (req, res) => {
    const alunos = await Aluno.find(); // Método para buscar alunos no banco
    res.render('listarAlunos', { alunos });
};

exports.formCadastro = (req, res) => {
    res.render('formCadastro');
};

exports.criarAluno = async (req, res) => {
    const novoAluno = new Aluno(req.body); // Cria um novo aluno com os dados do formulário
    await novoAluno.save(); // Salva no banco
    res.redirect('/alunos'); // Redireciona para a lista de alunos
};
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Lista de Alunos</title>
</head>
<body>
    <h1>Lista de Alunos</h1>
    <a href="/alunos/cadastrar">Cadastrar Novo Aluno</a>
    <ul>
        <% alunos.forEach(aluno => { %>
            <li><%= aluno.nome %> - <%= aluno.email %></li>
        <% }) %>
    </ul>
</body>
</html>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Cadastrar Aluno</title>
</head>
<body>
    <h1>Cadastrar Aluno</h1>
    <form action="/alunos" method="POST">
        <label for="nome">Nome:</label>
        <input type="text" id="nome" name="nome" required>
        <br>
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>
        <br>
        <button type="submit">Cadastrar</button>
    </form>
</body>
</html>
const mongoose = require('mongoose');

const alunoSchema = new mongoose.Schema({
    nome: { type: String, required: true },
    email: { type: String, required: true, unique: true }
});

const Aluno = mongoose.model('Aluno', alunoSchema);
module.exports = Aluno;
I’m @brunoalves1306
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
brunoalves1306/brunoalves1306 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
