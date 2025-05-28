# MAPA-UBS-
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Mapa Interativo - UBS Mãe Bernardina</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
    }

    #container {
      position: relative;
      display: inline-block;
    }

    #mapa-img {
      width: 100%;
      max-width: 800px;
      height: auto;
      border: 2px solid #444;
    }

    .casinha-wrapper {
      position: absolute;
      display: flex;
      align-items: center;
      gap: 4px;
      transform: translate(-50%, -100%);
      cursor: pointer;
    }

    .casinha {
      font-size: 24px;
    }

    .cor-circulo {
      width: 12px;
      height: 12px;
      border-radius: 50%;
      border: 1px solid #333;
    }

    .casinha-wrapper:hover::after {
      content: attr(data-nome);
      position: absolute;
      top: -25px;
      left: 50%;
      transform: translateX(-50%);
      background: #fff;
      border: 1px solid #999;
      padding: 4px 6px;
      border-radius: 4px;
      font-size: 12px;
      white-space: nowrap;
      z-index: 10;
    }
  </style>
</head>
<body>

  <h2>Mapa Interativo da UBS Mãe Bernardina</h2>
  <p>Clique no mapa para adicionar uma casinha. Clique em uma casinha para editar ou excluir.</p>

  <label for="tipoPaciente">Tipo de paciente:</label>
  <select id="tipoPaciente">
    <option value="roxo">Hipertenso (Roxo)</option>
    <option value="azul">Diabético (Azul)</option>
    <option value="amarelo">Gestante (Amarelo)</option>
    <option value="cinza">Domiciliado (Cinza)</option>
    <option value="branco">Criança &lt; 2 anos (Branco)</option>
    <option value="marrom">Câncer (Marrom)</option>
  </select>

  <div id="container">
    <img id="mapa-img" src="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxMSEhUTExMWFhUXFxgXGBcYGBgYFRgXFxcYGBgYFxcYHSggGB0lGxcXITEhJSkrLi4uFyAzODMtNygtLisBCgoKDg0OGxAQGy0lHyYtLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLf/AABEIAOEA4QMBEQACEQEDEQH/xAAbAAABBQEBAAAAAAAAAAAAAAAEAQIDBQYAB//EAEIQAAIBAgQEAwUEBgYBBQAAAAECAAMRBBIhMQUTQVEGImFxgZGhsQcUIzKx0SNS0eEjcoKSwhYkU1Oi4fEkNGNzgpOi/8QAGgEAAwEBAQEAAAAAAAAAAAAAAAECAwQFBv/EACERAQEBAQEAAgMBAAMBAAAAAAABEQISAyExBEEiUWFx/9oADAMBAAIRAxEAPwDTUAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAKsN1HEiSpE5rMTZtpbiuLz0NvZ6rWXsyGVieWNR0zT5U/cb7KFxoy9CPh+cU3RNu3KhMwnyea4btd+NnH9JmGTxGO55hvVLPfG3HRK5lxNZdVRU1PV1Zep9bmK5RpPjKcd5btYr5W7XTxVXGfTn07PGe7RW39mpc7s2MlVaUnbsz4N2qNMYXJcJ+L0+j6XV0ZPt4PBwUacFa7XmVvrKsmf7Nj3VFJ8T8k/UdAAAAAAAAAAAAAAAAAAAAAAAABQTxhThRWKXKztVKTdLT0XjP6z5by39lKM5euVxeIloybUrKnqt4x6dWa9HZUlO3g1NLdLlm19dtI1UekZ1ua1FLb6Mt9I1s2LVpR8K7HVm5Wvt4o5Lm0le1YqZVnNedqS6cf8AlL48PboquulPXF9ZeNerY8Tx9kF/R8K9C5U3W1pRmeJqvZRS1eyk3yTk85+6/X1wtdxtTX6zVt8TpRc+HX1tnm8qTb+ntzvKfGnN+Glr+Kc9+DLmRzjjLLqShTdUk5eLM4x+cvU8iVuXSt61ccUeFoQkmUrVjXZVKk+fuqz6U5KaXJra7+psTK3daXVnhLlGKReLRi7iYqe2bePMffzXueVqVy4Y3ep0k1jRbnblK0nOHUZZv2tcXVO3xkt0vWz6KiovThajam3VGm3l7Okpt3VOu7PL3GnvbfVvV8Fb9fBpUlOHi+OqNlFRVdPOxGKT1KrbNT3dU3KyV3So1SlqrqM77ufE0AAAAAAAAAAAAAAAAAAAAAAAAAAABmjs9b6LUZL2pyTq7OMcJZUbXM8WsuMoSq3bGpLdlk5fyM2tveaypr6L4bnpzHWoWpGWlP7LEv8AdExnCeOEb7Z/wBo+yXEJzYz0jNZsK3Kk0rkYvFRo2aRXFxqU7mlKeVpxW2tOr0d3VKz9ZzTS+HuvDLKMXFKnwr1akoxWqUZyUoUUoU4SmZwn3pQ3YsrqvbRV8X5/Mnbzf9HcUjRVatRd8oeGzRdQ8yWrOrWejoRWljVVST1LUlqbyUvKTeXPLUrrPHNPmoxbt8WXqNbKkoyXNXhRk0q0oqSSlW5ynNKNxySaTtVJpKblRp+UtL0tUpeXifhrRzZOKTe9rUJqqk7qlxuNPu4eH1+itw5yjqpmks+5nyU9Hp6JScfVOnxmpaFXV06vzeXZp1N7fbmpOvm3+nau+FGN4dr3S4R9JR04zV1RSe1dPTuX
