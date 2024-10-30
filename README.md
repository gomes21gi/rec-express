# rec-express

// Questão 1
app.post('/users/create', (req, res) => {
    const newUser = { id: users.length + 1, ...req.body };
    users.push(newUser);
    res.status(201).json(newUser);
});
      
app.get('/users/getAll', (req, res) => {
    res.status(200).json(users);
});

// a) Qual é o problema com o uso das rotas acima?
// b) Explique como o código pode ser ajustado para se adequar ao Nível 2.
// c) Corrija o código.

// Questão 2
app.delete('/users/:id', (req, res) => {
    const id = parseInt(req.params.id);
    const userIndex = users.findIndex(user => user.id === id);
    if (userIndex !== -1) {
        users.splice(userIndex, 1);
        res.json({ message: 'Usuário excluído' });
    } else {
        res.json({ message: 'Usuário não encontrado' });
    }
});

// a) Identifique o problema com os códigos de status HTTP usados no código.
// b) Corrija o código, adicionando os status HTTP adequados para uma resposta RESTful.

// Questão 3
app.put('/users/:id', (req, res) => {
    const id = parseInt(req.params.id);
    const user = users.find(user => user.id === id);
    if (user) {
        user.name = req.body.name;
        res.status(200).json(user);
    } else {
        res.status(404).json({ message: 'Usuário não encontrado' });
    }
});
   
// a) Explique a diferença entre os métodos PUT e PATCH em uma API REST.
// b) Corrija o código acima, implementando uma rota PATCH para permitir atualizações parciais.

// Questão 4
app.get('/users/:id', (req, res) => {
    const id = parseInt(req.params.id);
    const user = users.find(user => user.id === id);
    if (user) {
        res.status(200).json(user);
    } else {
        res.status(404).json({ message: 'Usuário não encontrado' });
    }
});
   
// a) Explique o que é HATEOAS e por que ele é importante no modelo REST.
// b) Altere o código para incluir links HATEOAS na resposta da API.

// Questão 5
app.get('/users/:id', (req, res) => {
    const id = req.params.id;
    const user = users.find(user => user.id === id);
    if (user) {
        res.status(200).json(user);
    } else {
        res.status(404).json({ message: 'Usuário não encontrado' });
    }
});

// a) Qual é o problema relacionado à validação nesse código?
// b) Corrija o código para incluir a validação adequada.

// Questão 6
app.post('/users', (req, res) => {
    const newUser = { id: users.length + 1, ...req.body };
    users.push(newUser);
    res.status(201).json(newUser);
});

// a) Qual é o problema de segurança com a falta de validação no corpo da requisição?
// b) Corrija o código para validar se o campo name está presente e atende a requisitos básicos, como ser uma string com pelo menos 3 caracteres.
