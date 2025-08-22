$conn = new mysqli('localhost', 'root', '', 'meubanco');

if ($conn->connect_error) {
  die("Conexão falhou: " . $conn->connect_error);
}

// Inserir um usuário
$sql = "INSERT INTO usuarios (nome, email) VALUES ('João', 'joao@example.com')";
if ($conn->query($sql) === TRUE) {
  echo "Usuário inserido com sucesso!";
} else {
  echo "Erro ao inserir usuário: " . $conn->error;
}

// Buscar usuários
$sql = "SELECT * FROM usuarios WHERE nome = 'João'";
$result = $conn->query($sql);
if ($result->num_rows > 0) {
  while($row = $result->fetch_assoc()) {
    echo "Nome: " . $row["nome"]. " - Email: " . $row["email"]. "<br>";
  }
} else {
  echo "Nenhum usuário encontrado.";
}
