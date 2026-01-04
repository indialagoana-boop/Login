# Login
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Hioram Martines</title>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500&family=Playfair+Display:wght@400;600&display=swap" rel="stylesheet">
  <style>
    *{margin:0;padding:0;box-sizing:border-box;}
    body{font-family:'Montserrat',sans-serif;background:#f5f5f3;color:#222;}
    html{scroll-behavior:smooth;}

    /* Tela de login */
    #loginScreen{
      position:fixed; top:0; left:0; width:100%; height:100%;
      background:rgba(0,0,0,0.8);
      display:flex; justify-content:center; align-items:center; z-index:1000;
    }
    #loginBox{
      background:#fff; padding:40px; border-radius:10px; text-align:center; width:300px;
    }
    #loginBox input{
      width:100%; padding:10px; margin:10px 0; border-radius:5px; border:1px solid #ccc;
    }
    #loginBox button{
      padding:10px 20px; margin-top:10px; border:none; background:#222; color:#fff; cursor:pointer; border-radius:5px; width:100%;
    }
    #loginBox h2{margin-bottom:20px; font-family:'Playfair Display',serif;}

    /* Header */
    header{
      min-height:100vh;
      background: linear-gradient(rgba(255,255,255,0.8), rgba(255,255,255,0.8)),
      url("fundo.jpg") center/cover no-repeat;
      display:flex; flex-direction:column; justify-content:center; align-items:center;
      text-align:center; padding:40px 20px;
    }
    header img{width:130px; margin-bottom:30px;}
    header h1{font-family:'Playfair Display',serif; font-size:3rem; letter-spacing:2px; margin-bottom:15px;}
    header p{font-size:1rem; letter-spacing:4px; text-transform:uppercase; color:#777;}

    /* Seções */
    section{max-width:900px; margin:auto; padding:100px 20px; text-align:center;}
    .impact{font-family:'Playfair Display',serif; font-size:2rem; margin-bottom:60px; cursor:pointer;}
    .about{font-size:1.05rem;color:#555;max-width:700px;margin:auto;margin-bottom:60px;line-height:1.8;transition:background 0.5s;padding:20px;border-radius:10px;}
    .buttons a{display:inline-block;margin:12px;padding:14px 36px;border:1px solid #222;text-decoration:none;color:#222;font-size:0.9rem;letter-spacing:2px;text-transform:uppercase;transition:0.3s;}
    .buttons a:hover{background:#222;color:#fff;}
    footer{background:#fff;padding:40px;text-align:center;font-size:0.8rem;color:#999;}

    /* Painel administrativo */
    .admin-panel{
      display:none;
      padding:50px;
      text-align:center;
      background:#f5f5f3;
      min-height:100vh;
    }
    .dashboard-cards{display:flex; flex-wrap:wrap; justify-content:center; gap:20px;}
    .card{
      background:#fff; padding:20px; border-radius:10px; box-shadow:0 5px 15px rgba(0,0,0,0.1);
      width:250px; text-align:left;
    }
    .card button{
      margin-top:10px; padding:10px 15px; border:none; background:#222; color:#fff; border-radius:5px; cursor:pointer;
    }
    .card button:hover{background:#555;}
    .admin-panel button#sairAdmin{margin-top:40px;padding:10px 20px;border:none;background:#777;color:#fff;border-radius:5px; cursor:pointer;}
    .admin-panel button#sairAdmin:hover{background:#444;}
  </style>
</head>
<body>

  <!-- Tela de login -->
  <div id="loginScreen">
    <div id="loginBox">
      <h2>Login</h2>
      <input type="text" id="usuario" placeholder="Usuário">
      <input type="password" id="senha" placeholder="Senha">
      <button onclick="fazerLogin()">Entrar</button>
    </div>
  </div>

  <!-- Conteúdo do site -->
  <div id="siteConteudo" style="display:none;">
    <header>
      <img src="logo.png" alt="Hioram Martines">
      <h1>HIORAM MARTINES</h1>
      <p>Marca pessoal • Estética • Presença</p>
    </header>

    <section>
      <div class="impact" onclick="mudarImpacto()">Elegância é quando a presença fala antes das palavras.</div>
      <div class="about" id="sobre">
        Hioram Martines é uma marca pessoal guiada pela estética,
        pelo cuidado com os detalhes e pela construção de uma identidade
        sofisticada, limpa e autêntica.  
        Cada escolha comunica. Cada presença permanece.
      </div>

      <div class="buttons">
        <a href="#" onclick="abrirInstagram()">Instagram</a>
        <a href="#" onclick="abrirWhatsApp()">WhatsApp</a>
        <a href="#" onclick="mudarCorSobre()">Mudar Fundo</a>
        <a href="#" onclick="abrirAdmin()">Painel Admin</a>
      </div>
    </section>

    <section>
      <h2>Experiência</h2>
      <p class="about">
        Atendimento focado em estética, presença e identidade.
        Cada detalhe pensado para transmitir sofisticação,
        cuidado e exclusividade.
      </p>
    </section>

    <footer>© 2026 · Hioram Martines</footer>
  </div>

  <!-- Painel administrativo -->
  <div class="admin-panel" id="adminPanel">
    <h2>Painel Administrativo</h2>
    <div class="dashboard-cards">
      <div class="card">
        <h3>Posts Recentes</h3>
        <p>Gerencie conteúdos e publicações.</p>
        <button onclick="alert('Abrir posts')">Ver Posts</button>
      </div>
      <div class="card">
        <h3>Contatos</h3>
        <p>Veja mensagens recebidas do WhatsApp/Instagram.</p>
        <button onclick="alert('Abrir contatos')">Ver Contatos</button>
      </div>
      <div class="card">
        <h3>Ajustes</h3>
        <p>Configure cores, frases e aparência do site.</p>
        <button onclick="alert('Abrir ajustes')">Abrir Ajustes</button>
      </div>
    </div>
    <button id="sairAdmin" onclick="sairAdmin()">Sair do Painel</button>
  </div>

  <script>
    // Login
    const usuarioCorreto = "Hioram";
    const senhaCorreta = "Guerra99";

    function fazerLogin(){
      const usuario = document.getElementById("usuario").value;
      const senha = document.getElementById("senha").value;
      if(usuario===usuarioCorreto && senha===senhaCorreta){
        document.getElementById("loginScreen").style.display="none";
        document.getElementById("siteConteudo").style.display="block";
      } else {
        alert("Usuário ou senha incorretos");
        document.getElementById("senha").value="";
      }
    }

    // Funções do site
    function abrirInstagram(){window.open("https://www.instagram.com/bruno_eu_hioram","_blank");}
    function abrirWhatsApp(){window.open("https://wa.me/message/PIVHCRXKTGIJL1","_blank");}
    function mudarImpacto(){
      const frases=["Elegância é quando a presença fala antes das palavras.","Detalhes fazem toda a diferença.","A sofisticação está na autenticidade.","Cada escolha comunica, cada presença permanece."];
      const impact=document.querySelector(".impact");
      let novaFrase=frases[Math.floor(Math.random()*frases.length)];
      while(novaFrase===impact.textContent){novaFrase=frases[Math.floor(Math.random()*frases.length)];}
      impact.textContent=novaFrase;
    }
    function mudarCorSobre(){
      const cores=["#f5f5f3","#ffe4e1","#d1ffd6","#cce7ff","#fff4b2"];
      const sobre=document.getElementById("sobre");
      let novaCor=cores[Math.floor(Math.random()*cores.length)];
      while(novaCor===sobre.style.backgroundColor){novaCor=cores[Math.floor(Math.random()*cores.length)];}
      sobre.style.backgroundColor=novaCor;
    }

    // Painel administrativo
    function abrirAdmin(){document.getElementById("adminPanel").style.display="block";}
    function sairAdmin(){document.getElementById("adminPanel").style.display="none";}
  </script>

</body>
</html>
