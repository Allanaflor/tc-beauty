<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes" />
    <title>TC Beauty - Loja Premium</title>

    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet" />
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />

    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Poppins', sans-serif; }
        body { background: #0a0a0a; color: #e0e0e0; overflow-x: hidden; -webkit-tap-highlight-color: transparent; }
        :root {
            --rosa: #FF1493; --rosa-claro: #FFC0CB; --rosa-glow: #ff4fa3; --rosa-escuro: #cc1470;
            --preto-fundo: #0a0a0a; --preto-card: #141414; --cinza-claro: #b0b0b0; --branco: #ffffff;
            --sombra-rosa: 0 10px 40px rgba(255, 20, 147, 0.25); --radius: 16px; --transition: 0.3s ease;
        }
        html { scroll-behavior: smooth; }
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: #1a1a1a; }
        ::-webkit-scrollbar-thumb { background: var(--rosa); border-radius: 10px; }

        #backToTop { position: fixed; bottom: 90px; right: 20px; width: 50px; height: 50px; border-radius: 50%;
            background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro)); color: white; border: none;
            font-size: 22px; cursor: pointer; opacity: 0; visibility: hidden; transition: var(--transition);
            box-shadow: var(--sombra-rosa); z-index: 998; }
        #backToTop.visible { opacity: 1; visibility: visible; }
        #backToTop:hover { transform: scale(1.1); }

        header { background: rgba(10, 10, 10, 0.95); backdrop-filter: blur(14px); padding: 12px 4%;
            display: flex; justify-content: space-between; align-items: center; position: sticky; top: 0;
            z-index: 1000; border-bottom: 1px solid rgba(255, 20, 147, 0.15); flex-wrap: wrap; gap: 10px; }
        .header-left { display: flex; align-items: center; gap: 12px; }
        .logo { font-size: 26px; font-weight: 700; background: linear-gradient(135deg, var(--rosa), var(--rosa-claro));
            -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
            text-shadow: 0 0 60px rgba(255, 20, 147, 0.2); letter-spacing: -0.5px; cursor: pointer; }
        .header-icons { display: flex; align-items: center; gap: 14px; color: #ccc; font-size: 18px; }
        .header-icons i { cursor: pointer; transition: var(--transition); position: relative; }
        .header-icons i:hover { color: var(--rosa); transform: scale(1.1); }
        .header-icons .cart-icon .badge, .header-icons .notif-icon .badge {
            position: absolute; top: -8px; right: -10px; background: var(--rosa); color: white; font-size: 9px;
            font-weight: 700; width: 18px; height: 18px; border-radius: 50%; display: flex;
            align-items: center; justify-content: center; }
        .header-icons .notif-icon .badge { background: #ffb400; }

        .pesquisa { display: flex; align-items: center; background: #1a1a1a; border-radius: 30px;
            padding: 3px 3px 3px 14px; border: 1px solid #2a2a2a; transition: var(--transition);
            flex: 1; max-width: 350px; min-width: 120px; }
        .pesquisa:focus-within { border-color: var(--rosa); box-shadow: 0 0 30px rgba(255, 20, 147, 0.08); }
        .pesquisa input { background: transparent; border: none; outline: none; color: #fff; padding: 8px 0;
            width: 100%; font-size: 13px; }
        .pesquisa input::placeholder { color: #666; }
        .pesquisa button { background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro)); border: none;
            padding: 8px 14px; border-radius: 30px; color: white; cursor: pointer; transition: var(--transition);
            font-size: 13px; }
        .pesquisa button:hover { transform: scale(1.04); box-shadow: 0 0 30px rgba(255, 20, 147, 0.2); }

        .menu-nav { display: flex; gap: 4px; flex-wrap: wrap; align-items: center; width: 100%;
            justify-content: center; padding-top: 8px; border-top: 1px solid rgba(255, 255, 255, 0.03); }
        .menu-nav .menu-btn { background: transparent; border: none; color: #aaa; padding: 6px 12px;
            border-radius: 30px; cursor: pointer; font-weight: 500; font-size: 12px; transition: var(--transition);
            position: relative; white-space: nowrap; text-decoration: none; display: inline-flex; align-items: center; }
        .menu-nav .menu-btn:hover { color: #fff; background: rgba(255, 20, 147, 0.08); }
        .menu-nav .menu-btn.active { color: #fff; background: rgba(255, 20, 147, 0.15);
            border: 1px solid rgba(255, 20, 147, 0.15); }
        .menu-nav .menu-btn i { margin-right: 4px; font-size: 12px; }
        
        /* ESTILO ESPECIAL PARA O BOTÃO AGENDAR NO MENU */
        .menu-nav .menu-btn.agendar-btn { 
            background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro)); 
            color: white; font-weight: 600; box-shadow: 0 4px 15px rgba(255, 20, 147, 0.3); 
        }
        .menu-nav .menu-btn.agendar-btn:hover { transform: scale(1.05); box-shadow: 0 6px 20px rgba(255, 20, 147, 0.5); }

        .page { display: none; animation: fadeIn 0.4s ease; }
        .page.active { display: block; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(15px); } to { opacity: 1; transform: translateY(0); } }

        .banner { padding: 30px 4%; background: radial-gradient(ellipse at 60% 30%, #1a0a12, #0a0a0a 75%);
            border-bottom: 1px solid rgba(255, 20, 147, 0.06); }
        .banner-slider { position: relative; overflow: hidden; border-radius: var(--radius); height: 320px; }
        .banner-slides { display: flex; width: 100%; height: 100%; transition: 0.7s ease; }
        .banner-slide { min-width: 100%; height: 100%; display: flex; align-items: center; justify-content: center;
            padding: 25px 30px; background: linear-gradient(135deg, #1a0a12, #0d0d0d);
            border: 1px solid rgba(255, 20, 147, 0.08); position: relative; }
        .banner-slide .slide-content { display: flex; align-items: center; justify-content: space-between;
            width: 100%; max-width: 1100px; gap: 20px; }
        .banner-slide .slide-text { flex: 1; }
        .banner-slide .slide-text h2 { font-size: 28px; color: #fff; margin-bottom: 8px; }
        .banner-slide .slide-text h2 span { background: linear-gradient(135deg, var(--rosa), var(--rosa-claro));
            -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
        .banner-slide .slide-text p { color: #aaa; font-size: 14px; margin-bottom: 16px; }
        .banner-slide .slide-text button { background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro));
            border: none; padding: 10px 24px; border-radius: 40px; color: white; font-weight: 600;
            cursor: pointer; transition: var(--transition); box-shadow: var(--sombra-rosa); font-size: 14px; }
        .banner-slide .slide-text button:hover { transform: scale(1.05);
            box-shadow: 0 8px 45px rgba(255, 20, 147, 0.35); }
        .banner-slide .slide-image { font-size: 60px; color: var(--rosa); opacity: 0.6;
            text-shadow: 0 0 80px rgba(255, 20, 147, 0.15); min-width: 80px; text-align: center; }

        .banner-btn { position: absolute; top: 50%; transform: translateY(-50%); background: rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(6px); color: white; border: 1px solid rgba(255, 255, 255, 0.05);
            width: 36px; height: 36px; border-radius: 50%; cursor: pointer; font-size: 14px;
            transition: var(--transition); z-index: 10; }
        .banner-btn:hover { background: var(--rosa); border-color: var(--rosa); }
        .banner-btn.prev { left: 10px; }
        .banner-btn.next { right: 10px; }

        .banner-dots { position: absolute; bottom: 14px; left: 50%; transform: translateX(-50%);
            display: flex; gap: 8px; z-index: 10; }
        .banner-dots span { width: 8px; height: 8px; border-radius: 50%; background: #444;
            cursor: pointer; transition: var(--transition); }
        .banner-dots span.active { background: var(--rosa); box-shadow: 0 0 20px rgba(255, 20, 147, 0.3);
            width: 24px; border-radius: 10px; }

        .section { padding: 35px 4%; }
        .section-dark { background: #0d0d0d; border-top: 1px solid rgba(255, 20, 147, 0.04);
            border-bottom: 1px solid rgba(255, 20, 147, 0.04); }

        .titulo { font-size: 24px; text-align: center; margin-bottom: 28px; color: #fff; position: relative; }
        .titulo::after { content: ''; display: block; width: 50px; height: 3px;
            background: linear-gradient(90deg, var(--rosa), var(--rosa-claro)); margin: 10px auto 0;
            border-radius: 4px; box-shadow: 0 0 30px rgba(255, 20, 147, 0.2); }
        .titulo i { color: var(--rosa); margin-right: 8px; }

        .categorias-grid { display: flex; justify-content: center; gap: 14px; flex-wrap: wrap; }
        .categoria-item { background: #141414; padding: 14px 18px; border-radius: var(--radius);
            display: flex; flex-direction: column; align-items: center; gap: 4px; cursor: pointer;
            transition: var(--transition); border: 1px solid rgba(255, 20, 147, 0.06); min-width: 70px; }
        .categoria-item:hover { transform: translateY(-4px); border-color: var(--rosa);
            box-shadow: var(--sombra-rosa); background: #1a1a1a; }
        .categoria-item i { font-size: 20px; color: var(--rosa); }
        .categoria-item span { color: #ccc; font-size: 11px; font-weight: 500; }

        .grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 18px; }
        .card { background: var(--preto-card); border-radius: var(--radius); overflow: hidden;
            transition: var(--transition); border: 1px solid rgba(255, 20, 147, 0.05); position: relative; }
        .card:hover { transform: translateY(-6px); border-color: rgba(255, 20, 147, 0.2);
            box-shadow: 0 15px 50px rgba(0, 0, 0, 0.5); }
        .card .card-image { position: relative; height: 180px; overflow: hidden; background: #0d0d0d; }
        .card .card-image img { width: 100%; height: 100%; object-fit: cover; transition: var(--transition); }
        .card:hover .card-image img { transform: scale(1.03); }
        .card .card-image .favorito { position: absolute; top: 8px; right: 8px; background: rgba(0, 0, 0, 0.6);
            backdrop-filter: blur(4px); width: 30px; height: 30px; border-radius: 50%; display: flex;
            align-items: center; justify-content: center; color: #888; cursor: pointer;
            transition: var(--transition); border: none; font-size: 13px; }
        .card .card-image .favorito:hover { color: var(--rosa); background: rgba(255, 20, 147, 0.15); }
        .card .card-image .favorito.ativo { color: var(--rosa); }
        .card .card-image .promo-tag { position: absolute; top: 8px; left: 8px;
            background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro)); color: white;
            font-size: 9px; font-weight: 700; padding: 2px 10px; border-radius: 30px;
            text-transform: uppercase; letter-spacing: 0.5px; }

        .card .info { padding: 12px 14px 14px; }
        .card .info .nome { font-size: 14px; font-weight: 600; color: #fff; margin-bottom: 2px; }
        .card .info .categoria-tag { font-size: 10px; color: var(--rosa-claro); opacity: 0.7; margin-bottom: 3px; }
        .card .info .preco { font-size: 17px; font-weight: 700;
            background: linear-gradient(135deg, var(--rosa), var(--rosa-claro));
            -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
            margin: 2px 0; }
        .card .info .preco-antigo { font-size: 11px; color: #666; text-decoration: line-through;
            margin-left: 4px; -webkit-text-fill-color: #666; }
        .card .info .parcelamento { font-size: 10px; color: #888; margin-bottom: 4px; }
        .card .info .avaliacao { display: flex; align-items: center; gap: 4px; margin-bottom: 6px; }
        .card .info .avaliacao .estrelas { color: #ffb400; font-size: 11px; }
        .card .info .avaliacao .qtd { color: #666; font-size: 10px; }
        .card .info .botoes-acoes { display: flex; gap: 4px; margin-top: 4px; }
        .card .info .botoes-acoes .btn { flex: 1; padding: 8px 6px; font-size: 11px; border: none;
            border-radius: 30px; font-weight: 600; cursor: pointer; transition: var(--transition); }
        .card .info .botoes-acoes .btn-comprar {
            background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro)); color: white; }
        .card .info .botoes-acoes .btn-comprar:hover { transform: scale(1.02);
            box-shadow: 0 8px 30px rgba(255, 20, 147, 0.2); }
        .card .info .botoes-acoes .btn-carrinho { background: transparent; border: 1.5px solid var(--rosa);
            color: var(--rosa); font-size: 13px; padding: 8px 10px; }
        .card .info .botoes-acoes .btn-carrinho:hover { background: var(--rosa); color: white; }

        /* ============================================================ */
        /* PÁGINA DE DETALHES DO PRODUTO - LAYOUT VERTICAL */
        /* ============================================================ */
        .produto-detalhes {
            max-width: 700px;
            margin: 0 auto;
            padding: 20px 0;
            display: flex;
            flex-direction: column;
            gap: 24px;
        }

        .produto-detalhes .imagem-principal-container {
            width: 100%;
            max-width: 500px;
            margin: 0 auto;
            aspect-ratio: 1 / 1;
            border-radius: var(--radius);
            overflow: hidden;
            background: #0d0d0d;
            border: 1px solid rgba(255, 20, 147, 0.1);
            position: relative;
        }

        .produto-detalhes .imagem-principal-container img {
            width: 100%;
            height: 100%;
            object-fit: contain;
            background: #141414;
            transition: transform 0.5s ease;
        }

        .produto-detalhes .imagem-principal-container:hover img {
            transform: scale(1.03);
        }

        .produto-detalhes .miniaturas-container {
            display: flex;
            gap: 10px;
            justify-content: center;
            flex-wrap: wrap;
            margin-top: 4px;
        }

        .produto-detalhes .miniaturas-container img {
            width: 70px;
            height: 70px;
            object-fit: cover;
            border-radius: 10px;
            cursor: pointer;
            border: 2px solid transparent;
            transition: all 0.3s ease;
            background: #1a1a1a;
            opacity: 0.6;
        }

        .produto-detalhes .miniaturas-container img:hover {
            opacity: 1;
            border-color: var(--rosa);
            transform: scale(1.05);
        }

        .produto-detalhes .miniaturas-container img.ativa {
            border-color: var(--rosa);
            opacity: 1;
            box-shadow: 0 0 20px rgba(255, 20, 147, 0.3);
        }

        .produto-detalhes-info {
            display: flex;
            flex-direction: column;
            gap: 16px;
            width: 100%;
        }

        .produto-detalhes-info .breadcrumb {
            color: #888; font-size: 12px; display: flex; align-items: center;
            gap: 6px; flex-wrap: wrap; justify-content: center; text-align: center; }
        .produto-detalhes-info .breadcrumb i { color: var(--rosa); }

        .produto-detalhes-info .nome-produto {
            font-size: 24px; color: #fff; font-weight: 700;
            line-height: 1.3; text-align: center; }

        .produto-detalhes-info .avaliacao-linha {
            display: flex; align-items: center; gap: 8px;
            font-size: 14px; justify-content: center; }
        .produto-detalhes-info .avaliacao-linha .estrelas { color: #ffb400; font-size: 16px; }
        .produto-detalhes-info .avaliacao-linha .vendidos { color: #888; font-size: 13px; }

        .produto-detalhes-info .preco-bloco {
            background: rgba(255, 20, 147, 0.05);
            border: 1px solid rgba(255, 20, 147, 0.15);
            border-radius: var(--radius);
            padding: 18px;
            text-align: center; }
        .produto-detalhes-info .preco-bloco .preco-antigo-grande {
            font-size: 14px; color: #666; text-decoration: line-through; }
        .produto-detalhes-info .preco-bloco .preco-grande {
            font-size: 32px; font-weight: 700;
            background: linear-gradient(135deg, var(--rosa), var(--rosa-claro));
            -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
            margin: 4px 0; }
        .produto-detalhes-info .preco-bloco .parcelas { color: #bbb; font-size: 14px; }
        .produto-detalhes-info .preco-bloco .desconto-tag {
            display: inline-block; background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro));
            color: white; font-size: 11px; font-weight: 700; padding: 3px 10px;
            border-radius: 20px; margin-left: 8px; text-transform: uppercase; }

        .produto-detalhes-info .descricao-produto {
            color: #bbb; font-size: 14px; line-height: 1.8;
            white-space: pre-line;
            background: #141414;
            padding: 20px;
            border-radius: var(--radius);
            border: 1px solid rgba(255, 20, 147, 0.05);
        }

        .produto-detalhes-info .titulo-secao {
            color: #fff; font-size: 15px; font-weight: 600; margin-bottom: 10px;
            display: flex; align-items: center; gap: 6px; }
        .produto-detalhes-info .titulo-secao i { color: var(--rosa); }

        .produto-detalhes-info .cores-opcoes {
            display: flex; gap: 10px; flex-wrap: wrap;
            background: #141414;
            padding: 18px;
            border-radius: var(--radius);
            border: 1px solid rgba(255, 20, 147, 0.05);
        }
        .produto-detalhes-info .cores-opcoes .cor-btn {
            padding: 10px 18px; border: 2px solid #2a2a2a; background: #1a1a1a; color: #ccc;
            border-radius: 30px; cursor: pointer; font-size: 13px; font-weight: 500;
            transition: all 0.3s ease; }
        .produto-detalhes-info .cores-opcoes .cor-btn:hover { border-color: var(--rosa); color: #fff; }
        .produto-detalhes-info .cores-opcoes .cor-btn.selecionada {
            background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro));
            border-color: var(--rosa); color: white; box-shadow: 0 4px 20px rgba(255, 20, 147, 0.3); }

        .produto-detalhes-info .acoes {
            display: flex; flex-direction: column; gap: 10px;
            margin-top: 4px; }
        .produto-detalhes-info .acoes .btn-principal {
            padding: 16px; background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro));
            color: white; border: none; border-radius: 30px; font-weight: 700; font-size: 16px;
            cursor: pointer; transition: all 0.3s ease;
            box-shadow: 0 4px 20px rgba(255, 20, 147, 0.25);
            display: flex; align-items: center; justify-content: center; gap: 8px; }
        .produto-detalhes-info .acoes .btn-principal:hover {
            transform: scale(1.02); box-shadow: 0 8px 35px rgba(255, 20, 147, 0.4); }
        .produto-detalhes-info .acoes .btn-secundario {
            padding: 14px; background: transparent; border: 2px solid var(--rosa); color: var(--rosa);
            border-radius: 30px; font-weight: 600; font-size: 15px; cursor: pointer;
            transition: all 0.3s ease; display: flex; align-items: center; justify-content: center; gap: 8px; }
        .produto-detalhes-info .acoes .btn-secundario:hover { background: var(--rosa); color: white; }

        .produto-detalhes-info .info-extras {
            display: flex; gap: 16px; flex-wrap: wrap; justify-content: center;
            margin-top: 6px; padding-top: 16px;
            border-top: 1px solid rgba(255, 255, 255, 0.05); }
        .produto-detalhes-info .info-extras .item-extra {
            display: flex; align-items: center; gap: 8px; color: #aaa; font-size: 13px; }
        .produto-detalhes-info .info-extras .item-extra i { color: var(--rosa); font-size: 15px; }

        .btn-voltar-produto {
            display: inline-flex; align-items: center; gap: 8px; background: transparent;
            border: 1px solid #2a2a2a; color: #ccc; padding: 10px 20px; border-radius: 30px;
            cursor: pointer; font-size: 13px; font-weight: 500; transition: all 0.3s ease; margin-bottom: 20px; }
        .btn-voltar-produto:hover { border-color: var(--rosa); color: var(--rosa); }

        /* ===== PÁGINA DE FAVORITOS ===== */
        .favoritos-vazios, .carrinho-vazio { text-align: center; padding: 40px 16px; color: #666; }
        .favoritos-vazios i, .carrinho-vazio i { font-size: 48px; color: #333; margin-bottom: 12px; }
        .favoritos-vazios h3, .carrinho-vazio h3 { color: #888; margin-bottom: 6px; font-size: 18px; }

        .notificacoes-lista { max-width: 700px; margin: 0 auto; }
        .notif-item { background: #141414; padding: 14px 16px; border-radius: var(--radius);
            border: 1px solid rgba(255, 20, 147, 0.05); margin-bottom: 10px; display: flex;
            align-items: flex-start; gap: 12px; transition: var(--transition); }
        .notif-item:hover { border-color: rgba(255, 20, 147, 0.1); }
        .notif-item .notif-icon { font-size: 18px; color: var(--rosa); margin-top: 2px; }
        .notif-item .notif-conteudo { flex: 1; }
        .notif-item .notif-conteudo .notif-titulo { color: #fff; font-weight: 600; font-size: 14px; }
        .notif-item .notif-conteudo .notif-texto { color: #aaa; font-size: 13px; }
        .notif-item .notif-conteudo .notif-data { color: #555; font-size: 11px; margin-top: 3px; }
        .notif-item .notif-lida { background: transparent; border: none; color: #555; cursor: pointer;
            font-size: 12px; transition: var(--transition); }
        .notif-item .notif-lida:hover { color: var(--rosa); }

        .conta-container { max-width: 500px; margin: 0 auto; text-align: center; }
        .conta-avatar { width: 100px; height: 100px; border-radius: 50%;
            background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro)); display: flex;
            align-items: center; justify-content: center; font-size: 40px; color: white;
            margin: 0 auto 16px; box-shadow: var(--sombra-rosa); position: relative;
            overflow: hidden; cursor: pointer; border: 3px solid rgba(255, 20, 147, 0.3);
            transition: var(--transition); }
        .conta-avatar:hover { border-color: var(--rosa); transform: scale(1.03); }
        .conta-avatar img { width: 100%; height: 100%; object-fit: cover; display: block; }
        .conta-avatar .camera-icon {
            position: absolute; bottom: 4px; right: 4px; background: var(--rosa);
            width: 30px; height: 30px; border-radius: 50%; display: flex;
            align-items: center; justify-content: center; font-size: 13px;
            color: white; border: 2px solid #141414;
            box-shadow: 0 2px 10px rgba(0,0,0,0.5); z-index: 2; }
        .conta-info { background: #141414; padding: 20px; border-radius: var(--radius);
            border: 1px solid rgba(255, 20, 147, 0.05); text-align: left; }
        .conta-info .campo { display: flex; justify-content: space-between; padding: 8px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.03); font-size: 14px; }
        .conta-info .campo:last-child { border-bottom: none; }
        .conta-info .campo .label { color: #888; }
        .conta-info .campo .valor { color: #fff; font-weight: 500; text-align: right; word-break: break-all; }
        .conta-logout { margin-top: 16px; background: transparent; border: 1px solid #ff1744;
            color: #ff1744; padding: 10px 24px; border-radius: 30px; cursor: pointer; font-weight: 600;
            transition: var(--transition); font-size: 14px; }
        .conta-logout:hover { background: #ff1744; color: white; }

        .carrinho-container { max-width: 800px; margin: 0 auto; }
        .carrinho-item { display: flex; align-items: center; gap: 12px; background: #141414;
            padding: 12px 14px; border-radius: var(--radius); border: 1px solid rgba(255, 20, 147, 0.05);
            margin-bottom: 10px; flex-wrap: wrap; }
        .carrinho-item img { width: 50px; height: 50px; border-radius: 10px; object-fit: cover; }
        .carrinho-item .info { flex: 1; min-width: 100px; }
        .carrinho-item .info .nome { color: #fff; font-weight: 500; font-size: 14px; }
        .carrinho-item .info .preco { color: var(--rosa); font-weight: 600; font-size: 14px; }
        .carrinho-item .qtd-control { display: flex; align-items: center; gap: 8px; }
        .carrinho-item .qtd-control button { background: #2a2a2a; border: none; color: white;
            width: 28px; height: 28px; border-radius: 50%; cursor: pointer; font-size: 14px;
            transition: var(--transition); }
        .carrinho-item .qtd-control button:hover { background: var(--rosa); }
        .carrinho-item .qtd-control span { color: #fff; font-weight: 500; min-width: 20px;
            text-align: center; font-size: 14px; }
        .carrinho-item .remover { background: transparent; border: none; color: #666; cursor: pointer;
            font-size: 16px; transition: var(--transition); }
        .carrinho-item .remover:hover { color: #ff1744; }
        .carrinho-resumo { background: #141414; padding: 20px; border-radius: var(--radius);
            border: 1px solid rgba(255, 20, 147, 0.05); margin-top: 16px; }
        .carrinho-resumo .linha { display: flex; justify-content: space-between; padding: 8px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.03); font-size: 14px; }
        .carrinho-resumo .linha:last-child { border-bottom: none; font-weight: 700; font-size: 16px; color: #fff; }
        .carrinho-resumo .linha .total { color: var(--rosa); }
        .carrinho-resumo .btn-finalizar { width: 100%; padding: 14px;
            background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro)); color: white;
            border: none; border-radius: 30px; font-weight: 700; font-size: 15px; cursor: pointer;
            transition: var(--transition); margin-top: 14px; }
        .carrinho-resumo .btn-finalizar:hover { transform: scale(1.02);
            box-shadow: 0 8px 35px rgba(255, 20, 147, 0.25); }

        .form-group { max-width: 600px; margin: 0 auto; }
        .form-group input, .form-group textarea, .form-group select { width: 100%; padding: 12px 16px;
            margin-bottom: 12px; border: 1px solid #2a2a2a; border-radius: 12px; font-size: 14px;
            transition: var(--transition); background: #141414; color: #e0e0e0; }
        .form-group input:focus, .form-group textarea:focus { border-color: var(--rosa);
            box-shadow: 0 0 30px rgba(255, 20, 147, 0.05); outline: none; }
        .form-group input::placeholder, .form-group textarea::placeholder { color: #666; }
        .form-group textarea { height: 100px; resize: vertical; }
        .form-group .btn { width: 100%; padding: 12px;
            background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro)); color: white;
            border: none; border-radius: 30px; font-weight: 600; font-size: 15px; cursor: pointer;
            transition: var(--transition); }
        .form-group .btn:hover { transform: scale(1.02);
            box-shadow: 0 8px 35px rgba(255, 20, 147, 0.2); }

        .avaliacoes-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(250px, 1fr)); gap: 16px; }
        .avaliacao-card { background: #141414; padding: 16px 18px; border-radius: var(--radius);
            border: 1px solid rgba(255, 20, 147, 0.05); transition: var(--transition); }
        .avaliacao-card:hover { border-color: rgba(255, 20, 147, 0.12); }
        .avaliacao-card .avaliacao-header { display: flex; justify-content: space-between;
            align-items: center; margin-bottom: 4px; flex-wrap: wrap; gap: 4px; }
        .avaliacao-card .avaliacao-header .nome { font-weight: 600; color: #fff; font-size: 14px; }
        .avaliacao-card .avaliacao-header .estrelas { color: #ffb400; font-size: 13px; }
        .avaliacao-card .avaliacao-header .data { font-size: 10px; color: #666; }
        .avaliacao-card p { color: #bbb; font-size: 13px; line-height: 1.6; }
        .avaliacao-card .curtir { margin-top: 8px; color: #666; font-size: 12px; cursor: pointer;
            transition: var(--transition); display: inline-flex; align-items: center; gap: 4px; }
        .avaliacao-card .curtir:hover { color: var(--rosa); }

        .feedbacks-lista { max-width: 600px; margin: 0 auto; display: flex; flex-direction: column; gap: 10px; }
        .feedback-item { background: #141414; padding: 12px 16px; border-radius: 12px;
            border: 1px solid rgba(255, 20, 147, 0.05); }
        .feedback-item .feedback-nome { color: var(--rosa); font-weight: 600; font-size: 14px; }
        .feedback-item .feedback-texto { color: #bbb; font-size: 13px; margin-top: 3px; }
        .feedback-item .feedback-responder { background: transparent; color: #666; border: none;
            font-size: 11px; cursor: pointer; margin-top: 4px; transition: var(--transition); }
        .feedback-item .feedback-responder:hover { color: var(--rosa); }

        /* ===== PÁGINAS INSTITUCIONAIS ===== */
        .institucional-container { max-width: 800px; margin: 0 auto; }
        .institucional-card {
            background: #141414; padding: 30px; border-radius: var(--radius);
            border: 1px solid rgba(255, 20, 147, 0.08); margin-bottom: 20px; line-height: 1.8; }
        .institucional-card h3 {
            color: var(--rosa); font-size: 20px; margin-bottom: 14px;
            display: flex; align-items: center; gap: 10px; }
        .institucional-card h4 {
            color: #fff; font-size: 16px; margin-top: 18px; margin-bottom: 8px; }
        .institucional-card p, .institucional-card li {
            color: #bbb; font-size: 14px; margin-bottom: 8px; }
        .institucional-card ul { padding-left: 20px; margin-bottom: 12px; }
        .institucional-card li { margin-bottom: 4px; }
        .institucional-card strong { color: #fff; }
        .institucional-card .destaque {
            background: rgba(255, 20, 147, 0.08); border-left: 3px solid var(--rosa);
            padding: 14px 18px; border-radius: 8px; margin: 14px 0; color: #fff; font-size: 14px; }
        .institucional-card .aviso {
            background: rgba(255, 23, 68, 0.08); border-left: 3px solid #ff1744;
            padding: 14px 18px; border-radius: 8px; margin: 14px 0; color: #fff; font-size: 14px; }
        .institucional-card .btn-ajuda {
            display: inline-flex; align-items: center; gap: 8px;
            background: linear-gradient(135deg, #25d366, #128c7e); color: white;
            padding: 12px 24px; border-radius: 30px; text-decoration: none;
            font-weight: 600; font-size: 15px; margin-top: 14px; transition: var(--transition); }
        .institucional-card .btn-ajuda:hover {
            transform: scale(1.05); box-shadow: 0 8px 30px rgba(37, 211, 102, 0.3); }

        .sobre-hero { text-align: center; padding: 20px 0 30px; }
        .sobre-hero .icone-grande {
            font-size: 60px; color: var(--rosa); margin-bottom: 14px;
            text-shadow: 0 0 40px rgba(255, 20, 147, 0.4); }
        .sobre-hero h3 { font-size: 24px; color: #fff; margin-bottom: 8px; }
        .sobre-hero p { color: #aaa; font-size: 15px; }

        .autoras-grid {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px; margin: 20px 0; }
        .autora-card {
            background: #1a1a1a; padding: 20px; border-radius: var(--radius);
            text-align: center; border: 1px solid rgba(255, 20, 147, 0.1); }
        .autora-card .avatar-autora {
            width: 70px; height: 70px; border-radius: 50%;
            background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro));
            display: flex; align-items: center; justify-content: center;
            font-size: 28px; color: white; margin: 0 auto 12px; box-shadow: var(--sombra-rosa); }
        .autora-card h4 { color: #fff; margin-bottom: 4px; font-size: 16px; }
        .autora-card p { color: #888; font-size: 13px; }

        footer { background: #0a0a0a; padding: 30px 4%; border-top: 1px solid rgba(255, 20, 147, 0.05);
            display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 20px; }
        footer .footer-col h4 { color: #fff; margin-bottom: 10px; font-size: 14px; }
        footer .footer-col p, footer .footer-col a { color: #777; font-size: 13px; line-height: 1.8;
            text-decoration: none; display: block; transition: var(--transition); cursor: pointer; }
        footer .footer-col a:hover { color: var(--rosa); }
        footer .footer-col .link-agendamento { color: var(--rosa); font-weight: 600; }
        footer .footer-col .link-agendamento:hover { color: var(--rosa-claro); }
        footer .footer-bottom { grid-column: 1 / -1; text-align: center; padding-top: 16px;
            border-top: 1px solid rgba(255, 255, 255, 0.03); color: #555; font-size: 12px; }

        .whatsapp-float { position: fixed; bottom: 16px; right: 16px; width: 54px; height: 54px;
            border-radius: 50%; background: linear-gradient(135deg, #25d366, #128c7e); display: flex;
            align-items: center; justify-content: center; font-size: 26px; color: white;
            text-decoration: none; box-shadow: 0 8px 35px rgba(37, 211, 102, 0.3);
            transition: var(--transition); z-index: 999; }
        .whatsapp-float:hover { transform: scale(1.08); box-shadow: 0 12px 50px rgba(37, 211, 102, 0.4); }

        /* BOTÃO FLUTUANTE DE AGENDAMENTO - FICA ACIMA DO WHATSAPP */
        .agendamento-float {
            position: fixed; bottom: 80px; right: 16px; width: 54px; height: 54px; border-radius: 50%;
            background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro)); display: flex;
            align-items: center; justify-content: center; font-size: 22px; color: white;
            text-decoration: none; box-shadow: 0 8px 35px rgba(255, 20, 147, 0.35);
            transition: var(--transition); z-index: 999; border: 2px solid rgba(255, 255, 255, 0.15); }
        .agendamento-float:hover { transform: scale(1.1); box-shadow: 0 12px 50px rgba(255, 20, 147, 0.5); }

        .modal-overlay { display: none; position: fixed; left: 0; top: 0; width: 100%; height: 100%;
            background: rgba(0, 0, 0, 0.85); backdrop-filter: blur(8px); justify-content: center;
            align-items: center; z-index: 9999; padding: 16px; }
        .modal-overlay.aberto { display: flex; }
        .modal-box { background: #141414; padding: 24px 20px; border-radius: 20px; width: 100%;
            max-width: 380px; text-align: center; border: 1px solid rgba(255, 20, 147, 0.1);
            box-shadow: 0 30px 80px rgba(0, 0, 0, 0.6); animation: modalFade 0.3s ease; }
        @keyframes modalFade { from { opacity: 0; transform: scale(0.92); } to { opacity: 1; transform: scale(1); } }
        .modal-box h2 { color: #fff; font-size: 20px; margin-bottom: 4px; }
        .modal-box .preco-modal { font-size: 22px; font-weight: 700;
            background: linear-gradient(135deg, var(--rosa), var(--rosa-claro));
            -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
            margin: 4px 0 14px; }
        .modal-box select { width: 100%; padding: 12px; border-radius: 30px; border: 1px solid #2a2a2a;
            background: #1a1a1a; color: #e0e0e0; font-size: 14px; margin: 6px 0 16px; }
        .modal-box select:focus { border-color: var(--rosa); outline: none; }
        .modal-box .btn { width: 100%; padding: 12px;
            background: linear-gradient(135deg, var(--rosa), var(--rosa-escuro)); color: white;
            border: none; border-radius: 30px; font-weight: 600; cursor: pointer;
            transition: var(--transition); font-size: 15px; }
        .modal-box .btn:hover { transform: scale(1.02); box-shadow: 0 8px 30px rgba(255, 20, 147, 0.2); }
        .modal-box .btn-fechar { background: transparent; color: #888; border: none; font-size: 14px;
            margin-top: 12px; cursor: pointer; transition: var(--transition); }
        .modal-box .btn-fechar:hover { color: #fff; }

        .toast { position: fixed; top: 16px; right: 16px; left: 16px; max-width: 350px;
            margin-left: auto; margin-right: auto; background: #141414;
            border: 1px solid rgba(255, 20, 147, 0.15); padding: 14px 18px; border-radius: 12px;
            color: #fff; box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5); z-index: 99999;
            transform: translateY(-120%); transition: 0.5s ease; }
        .toast.mostrar { transform: translateY(0); }
        .toast .toast-titulo { font-weight: 600; color: var(--rosa); font-size: 14px; }
        .toast .toast-texto { color: #aaa; font-size: 13px; }

        @media (max-width: 480px) {
            header { padding: 10px 3%; gap: 8px; }
            .logo { font-size: 20px; }
            .header-icons { gap: 10px; font-size: 16px; }
            .header-icons .cart-icon .badge, .header-icons .notif-icon .badge {
                font-size: 8px; width: 16px; height: 16px; top: -6px; right: -8px; }
            .pesquisa { max-width: 100%; min-width: 80px; padding: 2px 2px 2px 10px; }
            .pesquisa input { font-size: 12px; padding: 6px 0; }
            .pesquisa button { font-size: 12px; padding: 6px 12px; }
            .menu-nav { gap: 3px; padding-top: 6px; }
            .menu-nav .menu-btn { font-size: 10px; padding: 4px 8px; }
            .menu-nav .menu-btn i { font-size: 10px; margin-right: 3px; }
            .banner { padding: 20px 3%; }
            .banner-slider { height: 240px; }
            .banner-slide { padding: 16px 18px; }
            .banner-slide .slide-text h2 { font-size: 18px; }
            .banner-slide .slide-text p { font-size: 12px; margin-bottom: 12px; }
            .banner-slide .slide-text button { font-size: 12px; padding: 8px 18px; }
            .banner-slide .slide-image { font-size: 36px; min-width: 50px; }
            .banner-btn { width: 28px; height: 28px; font-size: 11px; }
            .banner-btn.prev { left: 6px; }
            .banner-btn.next { right: 6px; }
            .banner-dots span { width: 6px; height: 6px; }
            .banner-dots span.active { width: 18px; }
            .section { padding: 25px 3%; }
            .titulo { font-size: 20px; margin-bottom: 20px; }
            .titulo::after { width: 40px; height: 2px; margin-top: 8px; }
            .grid { grid-template-columns: repeat(2, 1fr); gap: 12px; }
            .card .card-image { height: 140px; }
            .card .info { padding: 10px 10px 12px; }
            .card .info .nome { font-size: 12px; }
            .card .info .preco { font-size: 14px; }
            .card .info .botoes-acoes .btn { font-size: 10px; padding: 6px 4px; }
            .card .info .botoes-acoes .btn-carrinho { font-size: 11px; padding: 6px 8px; }
            .categorias-grid { gap: 10px; }
            .categoria-item { padding: 10px 12px; min-width: 56px; }
            .categoria-item i { font-size: 16px; }
            .categoria-item span { font-size: 9px; }
            .avaliacoes-grid { grid-template-columns: 1fr; gap: 12px; }
            .carrinho-item { padding: 10px 12px; gap: 10px; }
            .carrinho-item img { width: 42px; height: 42px; }
            .carrinho-item .info .nome, .carrinho-item .info .preco { font-size: 12px; }
            .carrinho-item .qtd-control button { width: 24px; height: 24px; font-size: 12px; }
            .conta-avatar { width: 90px; height: 90px; font-size: 34px; }
            .notif-item { padding: 12px 14px; gap: 10px; }
            .notif-item .notif-conteudo .notif-titulo { font-size: 13px; }
            .notif-item .notif-conteudo .notif-texto { font-size: 12px; }
            .form-group input, .form-group textarea, .form-group select { padding: 10px 14px; font-size: 13px; }
            .form-group .btn { font-size: 14px; padding: 11px; }
            .modal-box { padding: 20px 16px; max-width: 320px; }
            .institucional-card { padding: 20px 16px; }
            .institucional-card h3 { font-size: 17px; }
            .institucional-card h4 { font-size: 14px; }
            .institucional-card p, .institucional-card li { font-size: 13px; }
            .sobre-hero .icone-grande { font-size: 44px; }
            .sobre-hero h3 { font-size: 20px; }
            .whatsapp-float { width: 48px; height: 48px; font-size: 22px; bottom: 14px; right: 14px; }
            .agendamento-float { width: 48px; height: 48px; font-size: 20px; bottom: 72px; right: 14px; }
            #backToTop { width: 40px; height: 40px; font-size: 18px; bottom: 130px; right: 14px; }
            footer { padding: 24px 3%; grid-template-columns: 1fr 1fr; gap: 16px; }

            .produto-detalhes-info .nome-produto { font-size: 20px; }
            .produto-detalhes-info .preco-bloco .preco-grande { font-size: 26px; }
            .produto-detalhes .imagem-principal-container { max-width: 100%; }
            .produto-detalhes .miniaturas-container img { width: 55px; height: 55px; }
        }

        @media (min-width: 481px) and (max-width: 768px) {
            .grid { grid-template-columns: repeat(2, 1fr); gap: 15px; }
            .card .card-image { height: 160px; }
            .banner-slider { height: 280px; }
            .banner-slide .slide-text h2 { font-size: 24px; }
            .banner-slide .slide-image { font-size: 50px; }
            .section { padding: 30px 4%; }
            .titulo { font-size: 22px; }
            .avaliacoes-grid { grid-template-columns: repeat(2, 1fr); }
        }

        @media (hover: none) {
            .card:hover, .categoria-item:hover { transform: none; }
            .card:hover .card-image img { transform: none; }
            .card .info .botoes-acoes .btn:active { transform: scale(0.95); }
            .categoria-item:active { transform: scale(0.95); }
        }
    </style>
</head>

<body>

    <div class="toast" id="toast">
        <div class="toast-titulo" id="toastTitulo">✨ Sucesso!</div>
        <div class="toast-texto" id="toastTexto">Ação realizada com sucesso.</div>
    </div>

    <header>
        <div class="header-left">
            <div class="logo" onclick="navegar('inicio')">TC Beauty</div>
            <div class="header-icons">
                <i class="fa-regular fa-heart" onclick="navegar('favoritos')" title="Favoritos"></i>
                <span class="notif-icon" onclick="navegar('notificacoes')" style="position:relative;cursor:pointer;">
                    <i class="fa-regular fa-bell"></i>
                    <span class="badge" id="notifBadge">0</span>
                </span>
                <i class="fa-regular fa-user" onclick="navegar('conta')" title="Minha Conta"></i>
                <span class="cart-icon" onclick="navegar('carrinho')" style="position:relative;cursor:pointer;">
                    <i class="fa-solid fa-bag-shopping"></i>
                    <span class="badge" id="carrinhoBadge">0</span>
                </span>
            </div>
        </div>

        <div class="pesquisa">
            <input type="text" id="campoPesquisa" placeholder="Pesquisar..." />
            <button id="btnPesquisa"><i class="fa-solid fa-search"></i></button>
        </div>

        <div class="menu-nav">
            <button class="menu-btn active" data-page="inicio" onclick="navegar('inicio')">
                <i class="fa-regular fa-house"></i> Início
            </button>
            <button class="menu-btn" data-page="produtos" onclick="navegar('produtos')">
                <i class="fa-regular fa-box"></i> Produtos
            </button>
            <button class="menu-btn" data-page="categorias" onclick="navegar('categorias')">
                <i class="fa-regular fa-grid-2"></i> Cat.
            </button>
            <button class="menu-btn" data-page="avaliacoes" onclick="navegar('avaliacoes')">
                <i class="fa-regular fa-star"></i> Avaliações
            </button>
            <button class="menu-btn" data-page="favoritos" onclick="navegar('favoritos')">
                <i class="fa-regular fa-heart"></i> Fav.
            </button>
            <button class="menu-btn" data-page="notificacoes" onclick="navegar('notificacoes')">
                <i class="fa-regular fa-bell"></i> Notif.
            </button>
            <button class="menu-btn" data-page="conta" onclick="navegar('conta')">
                <i class="fa-regular fa-user"></i> Conta
            </button>
            <button class="menu-btn" data-page="carrinho" onclick="navegar('carrinho')">
                <i class="fa-solid fa-bag-shopping"></i> Carr.
            </button>
            <!-- BOTÃO AGENDAR ADICIONADO AO MENU -->
            <a href="agendamento.html" class="menu-btn agendar-btn">
                <i class="fa-regular fa-calendar-check"></i> Agendar
            </a>
        </div>
    </header>

    <!-- ============================================================ -->
    <!-- PÁGINA: INÍCIO -->
    <!-- ============================================================ -->
    <div class="page active" id="page-inicio">

        <!-- ============================================================ -->
        <!-- 🎠 CARROSSEL - RENDERIZADO AUTOMATICAMENTE PELO JAVASCRIPT -->
        <!-- ============================================================ -->
        <section class="banner">
            <div class="banner-slider" id="bannerSlider">
                <div class="banner-slides" id="bannerSlides">
                    <!-- Os slides são inseridos automaticamente pelo JavaScript -->
                </div>
                <button class="banner-btn prev" onclick="moverBanner(-1)">❮</button>
                <button class="banner-btn next" onclick="moverBanner(1)">❯</button>
                <div class="banner-dots" id="bannerDots"></div>
            </div>
        </section>

        <section class="section">
            <h2 class="titulo"><i class="fa-regular fa-grid-2"></i> Categorias</h2>
            <div class="categorias-grid" id="categoriasGrid">
                <div class="categoria-item" onclick="filtrarPorCategoria('Batom')"><i class="fa-regular fa-palette"></i><span>Batom</span></div>
                <div class="categoria-item" onclick="filtrarPorCategoria('Base')"><i class="fa-regular fa-droplet"></i><span>Base</span></div>
                <div class="categoria-item" onclick="filtrarPorCategoria('Gloss')"><i class="fa-regular fa-flower"></i><span>Gloss</span></div>
                <div class="categoria-item" onclick="filtrarPorCategoria('Skincare')"><i class="fa-regular fa-wand-magic-sparkles"></i><span>Skincare</span></div>
                <div class="categoria-item" onclick="filtrarPorCategoria('Perfumes')"><i class="fa-regular fa-hand"></i><span>Perfumes</span></div>
                <div class="categoria-item" onclick="filtrarPorCategoria('Acessórios')"><i class="fa-regular fa-ring"></i><span>Acessórios</span></div>
                <div class="categoria-item" onclick="filtrarPorCategoria('Promoções')"><i class="fa-regular fa-tag"></i><span>Promoções</span></div>
                <div class="categoria-item" onclick="filtrarPorCategoria('Novidades')"><i class="fa-regular fa-sparkles"></i><span>Novidades</span></div>
            </div>
        </section>

        <section class="section section-dark">
            <h2 class="titulo"><i class="fa-regular fa-crown"></i> Destaques</h2>
            <div class="grid" id="gridDestaques"></div>
        </section>

        <section class="section section-dark">
            <h2 class="titulo"><i class="fa-regular fa-comment"></i> Feedback</h2>
            <div class="form-group">
                <input type="text" id="feedbackNome" placeholder="Seu nome" />
                <textarea id="feedbackTexto" placeholder="Escreva seu feedback sobre a loja..."></textarea>
                <button class="btn" id="btnEnviarFeedback"><i class="fa-regular fa-paper-plane"></i> Enviar Feedback</button>
            </div>
            <div class="feedbacks-lista" id="feedbacksLista" style="margin-top:30px;"></div>
        </section>
    </div>

    <!-- ============================================================ -->
    <!-- PÁGINA: PRODUTOS -->
    <!-- ============================================================ -->
    <div class="page" id="page-produtos">
        <section class="section">
            <h2 class="titulo"><i class="fa-regular fa-box"></i> Todos os Produtos</h2>
            <div class="grid" id="gridTodosProdutos"></div>
        </section>
    </div>

    <!-- ============================================================ -->
    <!-- PÁGINA: CATEGORIAS -->
    <!-- ============================================================ -->
    <div class="page" id="page-categorias">
        <section class="section">
            <h2 class="titulo"><i class="fa-regular fa-grid-2"></i> Categorias</h2>
            <div class="categorias-grid" id="categoriasGridFull"></div>
        </section>
    </div>

    <!-- ============================================================ -->
    <!-- PÁGINA: DETALHES DO PRODUTO -->
    <!-- ============================================================ -->
    <div class="page" id="page-produto">
        <section class="section">
            <div style="max-width:700px; margin:0 auto;">
                <button class="btn-voltar-produto" onclick="navegar('produtos')">
                    <i class="fa-solid fa-arrow-left"></i> Voltar aos produtos
                </button>
            </div>

            <div class="produto-detalhes" id="produtoDetalhes"></div>
        </section>
    </div>

    <!-- ============================================================ -->
    <!-- PÁGINA: AVALIAÇÕES -->
    <!-- ============================================================ -->
    <div class="page" id="page-avaliacoes">
        <section class="section">
            <h2 class="titulo"><i class="fa-regular fa-star"></i> Avaliações dos Clientes</h2>
            <p style="text-align:center; color:#aaa; font-size:14px; margin-bottom:24px;">
                Veja o que nossos clientes estão dizendo 💕
            </p>
            <div class="avaliacoes-grid" id="avaliacoesGrid"></div>
        </section>

        <section class="section section-dark">
            <h2 class="titulo"><i class="fa-regular fa-pen"></i> Deixe sua Avaliação</h2>
            <div class="form-group">
                <input type="text" id="avaliacaoNome" placeholder="Seu nome" />
                <div class="rating-input" id="ratingInput" style="display:flex; justify-content:center; gap:8px; font-size:28px; margin:10px 0 16px;">
                    <span data-nota="1" style="cursor:pointer; color:#333;">☆</span>
                    <span data-nota="2" style="cursor:pointer; color:#333;">☆</span>
                    <span data-nota="3" style="cursor:pointer; color:#333;">☆</span>
                    <span data-nota="4" style="cursor:pointer; color:#333;">☆</span>
                    <span data-nota="5" style="cursor:pointer; color:#333;">☆</span>
                </div>
                <input type="text" id="avaliacaoProduto" placeholder="Produto avaliado (opcional)" />
                <textarea id="avaliacaoTexto" placeholder="Escreva sua opinião sobre o produto..."></textarea>
                <button class="btn" id="btnEnviarAvaliacao"><i class="fa-regular fa-paper-plane"></i> Enviar Avaliação</button>
            </div>
        </section>
    </div>

    <!-- ============================================================ -->
    <!-- PÁGINA: FAVORITOS -->
    <!-- ============================================================ -->
    <div class="page" id="page-favoritos">
        <section class="section">
            <h2 class="titulo"><i class="fa-regular fa-heart"></i> Meus Favoritos</h2>
            <div id="favoritosContainer">
                <div class="favoritos-vazios" id="favoritosVazio">
                    <i class="fa-regular fa-heart"></i>
                    <h3>Nenhum favorito</h3>
                    <p>Clique no coração dos produtos para adicionar aos favoritos.</p>
                </div>
                <div class="grid" id="gridFavoritos"></div>
            </div>
        </section>
    </div>

    <!-- ============================================================ -->
    <!-- PÁGINA: NOTIFICAÇÕES -->
    <!-- ============================================================ -->
    <div class="page" id="page-notificacoes">
        <section class="section">
            <h2 class="titulo"><i class="fa-regular fa-bell"></i> Notificações</h2>
            <div class="notificacoes-lista" id="notificacoesLista"></div>
        </section>
    </div>

    <!-- ============================================================ -->
    <!-- PÁGINA: CONTA -->
    <!-- ============================================================ -->
    <div class="page" id="page-conta">
        <section class="section">
            <h2 class="titulo"><i class="fa-regular fa-user"></i> Minha Conta</h2>

            <div class="conta-container" id="contaCadastro" style="display:none;">
                <div class="conta-avatar" id="avatarCadastro" onclick="document.getElementById('inputFoto').click()">
                    <i class="fa-regular fa-user" id="avatarIcone"></i>
                    <img id="avatarPreview" src="" alt="Foto de perfil" style="display:none;" />
                    <div class="camera-icon"><i class="fa-solid fa-camera"></i></div>
                </div>
                <p style="color:#FF1493; font-size:12px; margin-bottom:15px; font-weight:600;">
                    <i class="fa-solid fa-camera"></i> Clique na bolinha para adicionar sua foto
                </p>
                <input type="file" id="inputFoto" accept="image/*" style="display:none;" onchange="previewFoto(event)" />

                <h3 style="color:#fff; margin-bottom:6px;">Crie sua conta</h3>
                <p style="color:#888; font-size:13px; margin-bottom:20px;">
                    Cadastre-se para acompanhar seus pedidos e favoritos.
                </p>

                <div class="conta-info">
                    <div class="form-group" style="margin:0;">
                        <label style="display:block; color:#ccc; font-size:13px; margin-bottom:5px; font-weight:600;">Nome completo *</label>
                        <input type="text" id="cadNome" placeholder="Digite seu nome completo" />

                        <label style="display:block; color:#ccc; font-size:13px; margin-bottom:5px; font-weight:600;">E-mail *</label>
                        <input type="email" id="cadEmail" placeholder="seu@email.com" />

                        <label style="display:block; color:#ccc; font-size:13px; margin-bottom:5px; font-weight:600;">Telefone / WhatsApp *</label>
                        <input type="tel" id="cadTelefone" placeholder="(13) 99999-9999" />

                        <button class="btn" id="btnCadastrar" style="margin-top:8px;">
                            <i class="fa-regular fa-circle-check"></i> Cadastrar
                        </button>
                    </div>
                </div>
            </div>

            <div class="conta-container" id="contaLogado" style="display:none;">
                <div class="conta-avatar" id="avatarLogado" onclick="trocarFotoLogado()">
                    <i class="fa-regular fa-user" id="avatarLogadoIcone"></i>
                    <img id="avatarLogadoPreview" src="" alt="Foto de perfil" style="display:none;" />
                    <div class="camera-icon"><i class="fa-solid fa-camera"></i></div>
                </div>
                <input type="file" id="inputFotoLogado" accept="image/*" style="display:none;" onchange="trocarFoto(event)" />
                <p style="color:#FF1493; font-size:12px; margin-bottom:15px; font-weight:600;">
                    <i class="fa-solid fa-camera"></i> Clique para trocar a foto
                </p>

                <div class="conta-info">
                    <div class="campo">
                        <span class="label">Nome</span>
                        <span class="valor" id="contaNome">—</span>
                    </div>
                    <div class="campo">
                        <span class="label">E-mail</span>
                        <span class="valor" id="contaEmail">—</span>
                    </div>
                    <div class="campo">
                        <span class="label">Telefone</span>
                        <span class="valor" id="contaTelefone">—</span>
                    </div>
                    <div class="campo">
                        <span class="label">Membro desde</span>
                        <span class="valor" id="contaData">—</span>
                    </div>
                </div>
                <button class="conta-logout" onclick="sairConta()">
                    <i class="fa-regular fa-right-from-bracket"></i> Sair da Conta
                </button>
            </div>
        </section>
    </div>

    <!-- ============================================================ -->
    <!-- PÁGINA: CARRINHO -->
    <!-- ============================================================ -->
    <div class="page" id="page-carrinho">
        <section class="section">
            <h2 class="titulo"><i class="fa-solid fa-bag-shopping"></i> Meu Carrinho</h2>
            <div class="carrinho-container">
                <div id="carrinhoVazio" class="carrinho-vazio">
                    <i class="fa-regular fa-cart-plus"></i>
                    <h3>Seu carrinho está vazio</h3>
                    <p>Adicione produtos clicando no botão <i class="fa-solid fa-cart-plus"></i> nos produtos.</p>
                </div>
                <div id="carrinhoItens"></div>
                <div class="carrinho-resumo" id="carrinhoResumo" style="display:none;">
                    <div class="linha"><span>Subtotal</span><span id="carrinhoSubtotal">R$ 0,00</span></div>
                    <div class="linha"><span>Taxa de entrega</span><span id="carrinhoFrete">R$ 4,00</span></div>
                    <div class="linha" style="font-weight:700;font-size:18px;border-bottom:none;">
                        <span>Total</span>
                        <span class="total" id="carrinhoTotal">R$ 4,00</span>
                    </div>
                    <button class="btn-finalizar" onclick="finalizarCompra()">
                        <i class="fa-brands fa-whatsapp"></i> Finalizar Compra
                    </button>
                </div>
            </div>
        </section>
    </div>

    <!-- ============================================================ -->
    <!-- PÁGINA: SOBRE A EMPRESA -->
    <!-- ============================================================ -->
    <div class="page" id="page-sobre">
        <section class="section">
            <h2 class="titulo"><i class="fa-regular fa-heart"></i> Sobre a TC Beauty</h2>
            <div class="institucional-container">
                <div class="institucional-card">
                    <div class="sobre-hero">
                        <div class="icone-grande"><i class="fa-regular fa-gem"></i></div>
                        <h3>Duas adolescentes, um sonho</h3>
                        <p>Uma história de garra, amizade e muita vontade de vencer</p>
                    </div>

                    <p>
                        A <strong>TC Beauty</strong> nasceu do sonho de duas adolescentes que sempre acreditaram
                        que poderiam mudar de vida através do próprio esforço. Somos jovens, determinadas e cheias
                        de vontade de crescer, e foi com muito trabalho, criatividade e amor por maquiagem que
                        decidimos empreender.
                    </p>

                    <p>
                        Cada produto que vendemos carrega um pouco da nossa história. Não somos uma grande empresa —
                        somos duas meninas que resolveram <strong>correr atrás dos próprios sonhos</strong> e provar
                        que idade não é obstáculo para quem tem determinação.
                    </p>

                    <div class="destaque">
                        <i class="fa-solid fa-quote-left" style="color:var(--rosa); margin-right:6px;"></i>
                        Nosso maior desejo é mostrar que, com foco e trabalho duro, é possível conquistar
                        um futuro melhor. E você, cliente, faz parte dessa jornada!
                    </div>

                    <h4>Nossa Missão</h4>
                    <p>
                        Oferecer produtos de maquiagem de qualidade a preços acessíveis, atendendo com carinho
                        cada cliente que confia em nós, e mostrar que sonhos podem se tornar realidade.
                    </p>

                    <h4>Nossos Valores</h4>
                    <ul>
                        <li><strong>Determinação:</strong> Não desistimos fácil.</li>
                        <li><strong>Carinho:</strong> Cada cliente é tratada como família.</li>
                        <li><strong>Qualidade:</strong> Produtos selecionados com cuidado.</li>
                        <li><strong>Sonho:</strong> Acreditamos que tudo é possível.</li>
                    </ul>

                    <div class="autoras-grid">
                        <div class="autora-card">
                            <div class="avatar-autora"><i class="fa-solid fa-user"></i></div>
                            <h4>Fundadora 1</h4>
                            <p>Sonhadora e dedicada</p>
                        </div>
                        <div class="autora-card">
                            <div class="avatar-autora"><i class="fa-solid fa-user"></i></div>
                            <h4>Fundadora 2</h4>
                            <p>Esforçada e criativa</p>
                        </div>
                    </div>

                    <p style="text-align:center; color: var(--rosa); font-weight:600; margin-top:20px;">
                        💕 Obrigada por fazer parte da nossa história! 💕
                    </p>
                </div>
            </div>
        </section>
    </div>

    <!-- ============================================================ -->
    <!-- PÁGINA: POLÍTICA DE PRIVACIDADE -->
    <!-- ============================================================ -->
    <div class="page" id="page-politica">
        <section class="section">
            <h2 class="titulo"><i class="fa-regular fa-shield"></i> Política de Privacidade</h2>
            <div class="institucional-container">
                <div class="institucional-card">
                    <p>
                        Na <strong>TC Beauty</strong>, a sua privacidade é muito importante para nós.
                        Esta Política de Privacidade explica como coletamos, usamos e protegemos as suas informações.
                    </p>

                    <h4>1. Informações que coletamos</h4>
                    <ul>
                        <li>Nome completo</li>
                        <li>E-mail</li>
                        <li>Telefone / WhatsApp</li>
                        <li>Endereço de entrega (informado no momento da compra)</li>
                        <li>Foto de perfil (opcional, fornecida por você)</li>
                    </ul>

                    <h4>2. Como usamos suas informações</h4>
                    <ul>
                        <li>Para processar e entregar seus pedidos</li>
                        <li>Para entrar em contato pelo WhatsApp sobre a compra</li>
                        <li>Para personalizar sua experiência na loja</li>
                        <li>Para enviar promoções e novidades (apenas se você permitir)</li>
                    </ul>

                    <h4>3. Compartilhamento de dados</h4>
                    <p>
                        <strong>Não compartilhamos</strong> seus dados com terceiros, exceto quando
                        necessário para a entrega do produto (como o serviço de transporte).
                    </p>

                    <h4>4. Segurança</h4>
                    <p>
                        Seus dados ficam armazenados no próprio navegador do seu dispositivo. Não temos acesso
                        a essas informações sem a sua autorização, e você pode removê-las a qualquer momento
                        saindo da sua conta.
                    </p>

                    <h4>5. Seus direitos</h4>
                    <ul>
                        <li>Solicitar a exclusão dos seus dados</li>
                        <li>Corrigir informações incorretas</li>
                        <li>Cancelar notificações e promoções</li>
                    </ul>

                    <div class="destaque">
                        Ao usar nosso site, você concorda com esta política.
                        Em caso de dúvidas, entre em contato pelo nosso WhatsApp.
                    </div>

                    <p style="text-align:center; color:#888; font-size:12px; margin-top:20px;">
                        Última atualização: 2026
                    </p>
                </div>
            </div>
        </section>
    </div>

    <!-- ============================================================ -->
    <!-- PÁGINA: TERMOS DE USO -->
    <!-- ============================================================ -->
    <div class="page" id="page-termos">
        <section class="section">
            <h2 class="titulo"><i class="fa-regular fa-file-lines"></i> Termos de Uso</h2>
            <div class="institucional-container">
                <div class="institucional-card">
                    <p>
                        Bem-vinda à <strong>TC Beauty</strong>! Ao utilizar nosso site, você concorda com os
                        termos e condições descritos abaixo. Leia com atenção antes de fazer sua compra.
                    </p>

                    <h4>1. Uso do site</h4>
                    <p>
                        O site da TC Beauty é destinado a maiores de 18 anos ou menores acompanhados de
                        responsável. Você se compromete a fornecer informações verdadeiras no momento do cadastro.
                    </p>

                    <h4>2. Produtos e preços</h4>
                    <ul>
                        <li>Todos os produtos são descritos com o máximo de detalhes possível.</li>
                        <li>Os preços podem ser alterados sem aviso prévio.</li>
                        <li>As imagens são ilustrativas e podem sofrer pequenas variações de cor.</li>
                    </ul>

                    <h4>3. Pedidos e pagamentos</h4>
                    <ul>
                        <li>Os pedidos são finalizados pelo WhatsApp.</li>
                        <li>Formas de pagamento: Pix, cartão de crédito e boleto.</li>
                        <li>O pedido só é confirmado após o pagamento.</li>
                    </ul>

                    <h4>4. Taxa de entrega</h4>
                    <p>
                        A taxa de entrega é fixa em <strong>R$ 4,00</strong> para todas as regiões atendidas.
                    </p>

                    <h4>5. Responsabilidades</h4>
                    <p>
                        A TC Beauty não se responsabiliza por atrasos causados por transportadoras, greves,
                        condições climáticas ou força maior. Nosso compromisso é sempre enviar seu produto o
                        mais rápido possível.
                    </p>

                    <div class="destaque">
                        Ao efetuar uma compra, você declara que leu e aceitou todos os termos acima.
                        Obrigada por confiar na TC Beauty! 💕
                    </div>

                    <p style="text-align:center; color:#888; font-size:12px; margin-top:20px;">
                        Última atualização: 2026
                    </p>
                </div>
            </div>
        </section>
    </div>

    <!-- ============================================================ -->
    <!-- PÁGINA: TROCAS E DEVOLUÇÕES -->
    <!-- ============================================================ -->
    <div class="page" id="page-trocas">
        <section class="section">
            <h2 class="titulo"><i class="fa-regular fa-arrows-rotate"></i> Trocas e Devoluções</h2>
            <div class="institucional-container">
                <div class="institucional-card">
                    <div class="aviso">
                        <strong>⚠️ ATENÇÃO:</strong> A TC Beauty <strong>NÃO realiza trocas nem devoluções</strong> de
                        produtos, salvo em casos de defeito de fabricação comprovado.
                    </div>

                    <h4>Por que não fazemos trocas?</h4>
                    <p>
                        Por se tratar de produtos de beleza e maquiagem (itens de uso pessoal e higiene), 
                        conforme as normas da <strong>Anvisa</strong> e do <strong>Código de Defesa do Consumidor</strong>,
                        <strong>não é permitida a troca ou devolução</strong> de produtos que já foram abertos ou
                        utilizados, por questões de segurança e saúde.
                    </p>

                    <h4>O que fazer em caso de defeito?</h4>
                    <ul>
                        <li>Entre em contato pelo WhatsApp em até <strong>7 dias</strong> após o recebimento.</li>
                        <li>Envie fotos ou vídeos mostrando o defeito do produto.</li>
                        <li>Vamos analisar o caso e, se comprovado o defeito de fabricação, faremos a substituição.</li>
                    </ul>

                    <h4>O que NÃO é considerado defeito:</h4>
                    <ul>
                        <li>Cor diferente do esperado (as imagens são ilustrativas).</li>
                        <li>Preferência pessoal pelo produto.</li>
                        <li>Produto já aberto ou usado.</li>
                        <li>Danos causados por mau uso.</li>
                    </ul>

                    <h4>Importante</h4>
                    <p>
                        Antes de finalizar a compra, confira atentamente as descrições, cores e características
                        dos produtos. Em caso de dúvida, entre em contato pelo WhatsApp antes de comprar —
                        teremos prazer em te ajudar! 💕
                    </p>

                    <div class="destaque">
                        <i class="fa-solid fa-heart" style="color:var(--rosa); margin-right:6px;"></i>
                        Nossa prioridade é a sua satisfação. Se tiver qualquer problema, fale com a gente —
                        estamos aqui para ajudar!
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- ============================================================ -->
    <!-- PÁGINA: CENTRAL DE AJUDA -->
    <!-- ============================================================ -->
    <div class="page" id="page-ajuda">
        <section class="section">
            <h2 class="titulo"><i class="fa-regular fa-headset"></i> Central de Ajuda</h2>
            <div class="institucional-container">
                <div class="institucional-card" style="text-align:center;">
                    <div class="sobre-hero">
                        <div class="icone-grande"><i class="fa-regular fa-circle-question"></i></div>
                        <h3>Como podemos te ajudar?</h3>
                        <p>Estamos sempre disponíveis para atender você</p>
                    </div>

                    <p>
                        Se você tem dúvidas sobre produtos, pedidos, entregas ou qualquer outra coisa,
                        nossa equipe está pronta para te ajudar pelo WhatsApp!
                    </p>

                    <h4 style="text-align:left;">Dúvidas mais comuns:</h4>
                    <ul style="text-align:left;">
                        <li><strong>Como faço um pedido?</strong> Escolha os produtos, adicione ao carrinho e finalize pelo WhatsApp.</li>
                        <li><strong>Qual o prazo de entrega?</strong> De 3 a 7 dias úteis após a confirmação do pagamento.</li>
                        <li><strong>Quanto custa o frete?</strong> Taxa fixa de R$ 4,00 para todas as regiões.</li>
                        <li><strong>Quais as formas de pagamento?</strong> Pix, cartão de crédito e boleto.</li>
                        <li><strong>Posso trocar um produto?</strong> Não realizamos trocas, apenas em caso de defeito de fabricação.</li>
                        <li><strong>Como rastrear meu pedido?</strong> Enviamos o código de rastreio pelo WhatsApp.</li>
                    </ul>

                    <h4 style="text-align:left;">Ainda com dúvidas?</h4>
                    <p style="text-align:left;">
                        Clique no botão abaixo para falar diretamente com a gente pelo WhatsApp.
                        Atendimento de segunda a sábado, das 9h às 20h.
                    </p>

                    <a href="https://wa.me/5513992084636?text=Ol%C3%A1%2C%20preciso%20de%20ajuda%20com%20a%20TC%20Beauty!" 
                       target="_blank" 
                       class="btn-ajuda">
                        <i class="fa-brands fa-whatsapp"></i> Falar no WhatsApp
                    </a>

                    <div style="margin-top:24px; padding-top:20px; border-top:1px solid rgba(255,255,255,0.05);">
                        <p style="color:#888; font-size:13px;">
                            <i class="fa-regular fa-clock" style="color:var(--rosa);"></i> 
                            Atendimento: Seg a Sáb, 9h às 20h
                        </p>
                        <p style="color:#888; font-size:13px;">
                            <i class="fa-regular fa-envelope" style="color:var(--rosa);"></i> 
                            E-mail: tcbeauty@gmail.com
                        </p>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- ============================================================ -->
    <!-- RODAPÉ -->
    <!-- ============================================================ -->
    <footer>
        <div class="footer-col">
            <h4>TC Beauty</h4>
            <p>Sua beleza começa aqui. Produtos premium com a qualidade que você merece.</p>
        </div>
        <div class="footer-col">
            <h4>Institucional</h4>
            <a onclick="navegar('sobre')">Sobre a empresa</a>
            <a onclick="navegar('politica')">Política de Privacidade</a>
            <a onclick="navegar('termos')">Termos de Uso</a>
            <a onclick="navegar('trocas')">Trocas e Devoluções</a>
        </div>
        <div class="footer-col">
            <h4>Serviços</h4>
            <a onclick="navegar('ajuda')">
                <i class="fa-regular fa-circle-question"></i> Central de Ajuda
            </a>
            <a href="agendamento.html" class="link-agendamento">
                <i class="fa-regular fa-calendar-check"></i> Agendar Atendimento
            </a>
            <a onclick="navegar('avaliacoes')">Avaliações</a>
        </div>
        <div class="footer-col">
            <h4>Atendimento</h4>
            <a href="https://wa.me/5513992084636">WhatsApp</a>
            <a href="mailto:tcbeauty@gmail.com">E-mail</a>
        </div>
        <div class="footer-col">
            <h4>Formas de Pagamento</h4>
            <p>Pix • Cartão • Boleto</p>
            <p style="margin-top:8px;font-size:12px;color:#555;">Taxa de entrega: R$ 4,00</p>
        </div>
        <div class="footer-bottom">
            © 2026 TC Beauty - Todos os direitos reservados. <span style="color:var(--rosa);">♥</span>
        </div>
    </footer>

    <!-- BOTÃO FLUTUANTE DO WHATSAPP (FICA EMBAIXO) -->
    <a href="https://wa.me/5513992084636" target="_blank" class="whatsapp-float">
        <i class="fa-brands fa-whatsapp"></i>
    </a>

    <!-- BOTÃO FLUTUANTE DE AGENDAMENTO (FICA EM CIMA DO WHATSAPP) -->
    <a href="agendamento.html" class="agendamento-float" title="Agendar Atendimento">
        <i class="fa-regular fa-calendar-check"></i>
    </a>

    <button id="backToTop" onclick="window.scrollTo({top:0,behavior:'smooth'})">
        <i class="fa-solid fa-arrow-up"></i>
    </button>

    <div class="modal-overlay" id="modalProduto">
        <div class="modal-box">
            <h2 id="modalNome">Produto</h2>
            <p class="preco-modal" id="modalPreco">R$ 0,00</p>
            <label style="display:block;font-weight:500;margin-bottom:4px;color:#aaa;">Escolha a cor:</label>
            <select id="modalCor">
                <option value="Tom 01">Tom 01</option>
                <option value="Tom 02">Tom 02</option>
                <option value="Tom 03">Tom 03</option>
                <option value="Tom 04">Tom 04</option>
                <option value="Tom 05">Tom 05</option>
                <option value="Tom 06">Tom 06</option>
            </select>
            <button class="btn" id="modalComprar"><i class="fa-brands fa-whatsapp"></i> Comprar no WhatsApp</button>
            <button class="btn-fechar" id="modalFechar">Fechar</button>
        </div>
    </div>

    <script>
        // ================================================================
        // TC BEAUTY - SCRIPT COMPLETO
        // ================================================================

        // ================================================================
        // 🎠 CARROSSEL - CONFIGURAÇÃO DOS SLIDES
        // ================================================================
        const carrosselSlides = [
            {
                titulo: 'Coleção',
                destaque: 'Luxo',
                subtitulo: 'Descubra os produtos mais exclusivos da TC Beauty.',
                textoBotao: 'Explorar',
                iconeBotao: 'fa-crown',
                iconeSlide: 'fa-gem',
                acao: 'produtos'
            },
            {
                titulo: 'Até',
                destaque: '50% OFF',
                subtitulo: 'Promoções imperdíveis nos produtos mais amados.',
                textoBotao: 'Ver Ofertas',
                iconeBotao: 'fa-tag',
                iconeSlide: 'fa-star',
                acao: 'produtos'
            },
            {
                titulo: 'Novidades',
                destaque: 'Gloss & Batom',
                subtitulo: 'As últimas tendências em maquiagem chegaram na TC Beauty.',
                textoBotao: 'Lançamentos',
                iconeBotao: 'fa-sparkles',
                iconeSlide: 'fa-moon',
                acao: 'produtos'
            },
            {
                titulo: 'Agende seu',
                destaque: 'Atendimento',
                subtitulo: 'Maquiagem profissional, consultoria e cuidados exclusivos com hora marcada.',
                textoBotao: 'Agendar Agora',
                iconeBotao: 'fa-calendar-check',
                iconeSlide: 'fa-calendar-check',
                acao: 'agendar' // Esta ação abre o agendamento.html
            }
        ];

        // ================================================================
        // 📦 BANCO DE PRODUTOS - TC BEAUTY
        // ================================================================
        const produtos = [
            { id:1, nome:'Base Matte Premium', preco:'R$ 15,00', precoNum:15.00, precoAntigo:'R$ 25,00',
              imagens:['base1-1.jpg','base1-2.jpg','base1-3.jpg','base1-4.jpg','base1-5.jpg','base1-6.jpg','base1-7.jpg'],
              descricao:'A Base Matte Premium da TC Beauty oferece cobertura impecável com efeito matte aveludado que dura o dia inteiro. Sua fórmula leve e oil-free controla a oleosidade, deixando a pele uniforme e natural. Ideal para todos os tipos de pele.\n\n✔ Alta cobertura\n✔ Efeito matte aveludado\n✔ Longa duração (até 12h)\n✔ Não obstrui os poros\n✔ Disponível em 6 tons',
              categoria:'Base', destaque:true, vendidos:342, parcelas:'3x de R$ 5,00' },
            { id:5, nome:'Base Iluminadora', preco:'R$ 15,00', precoNum:15.00, precoAntigo:'R$ 25,00',
              imagens:['base2-1.jpg','base2-2.jpg','base2-3.jpg','base2-4.jpg','base2-5.jpg','base2-6.jpg','base2-7.jpg'],
              descricao:'A Base Iluminadora TC Beauty deixa sua pele com aquele glow saudável e natural. Fórmula com partículas iluminadoras que realçam o contorno do rosto.\n\n✔ Efeito luminoso\n✔ Cobertura média\n✔ Textura leve\n✔ Ideal para pele seca e normal\n✔ Acabamento radiante',
              categoria:'Base', destaque:false, vendidos:89, parcelas:'3x de R$ 5,00' },
            { id:8, nome:'Pó Compacto Premium', preco:'R$ 15,00', precoNum:15.00, precoAntigo:null,
              imagens:['po1-1.jpg','po1-2.jpg','po1-3.jpg','po1-4.jpg','po1-5.jpg','po1-6.jpg','po1-7.jpg'],
              descricao:'Pó Compacto Premium com textura fina que sela a maquiagem e controla o brilho. Acabamento natural e aveludado.\n\n✔ Selagem perfeita\n✔ Controle de oleosidade\n✔ Acabamento natural\n✔ Compacto prático\n✔ Fácil de transportar',
              categoria:'Base', destaque:false, vendidos:98, parcelas:'3x de R$ 5,00' },
            { id:10, nome:'Base Líquida Natural', preco:'R$ 15,00', precoNum:15.00, precoAntigo:'R$ 25,00',
              imagens:['base3-1.jpg','base3-2.jpg','base3-3.jpg','base3-4.jpg','base3-5.jpg','base3-6.jpg','base3-7.jpg'],
              descricao:'Base líquida com efeito natural que uniformiza o tom da pele sem pesar. Perfeita para o dia a dia.\n\n✔ Efeito natural\n✔ Cobertura leve a média\n✔ Textura fluida\n✔ Fácil de espalhar\n✔ Para todos os tipos de pele',
              categoria:'Base', destaque:false, vendidos:112, parcelas:'3x de R$ 5,00' },
            { id:13, nome:'Base Matte Soft', preco:'R$ 15,00', precoNum:15.00, precoAntigo:'R$ 25,00',
              imagens:['base4-1.jpg','base4-2.jpg','base4-3.jpg','base4-4.jpg','base4-5.jpg','base4-6.jpg','base4-7.jpg'],
              descricao:'Base Matte Soft com textura suave que se adapta à pele, deixando-a uniforme e com aparência natural.\n\n✔ Efeito matte suave\n✔ Cobertura média\n✔ Longa duração\n✔ Não craquela\n✔ Fácil aplicação',
              categoria:'Base', destaque:false, vendidos:67, parcelas:'3x de R$ 5,00' },
            { id:16, nome:'Corretivo Líquido Melu by Ruby Rose', preco:'R$ 10,00', precoNum:10.00, precoAntigo:null,
              imagens:['melu-1.jpg','melu-2.jpg','melu-3.jpg','melu-4.jpg','melu-5.jpg','melu-6.jpg','melu-7.jpg'],
              descricao:'Corretivo Líquido Melu by Ruby Rose com alta cobertura para disfarçar olheiras, manchas e imperfeições. Fórmula cremosa e de longa duração.\n\n✔ Alta cobertura\n✔ Acabamento natural\n✔ Longa duração\n✔ Não marca linhas de expressão\n✔ Aplicador prático',
              categoria:'Base', destaque:false, vendidos:92, parcelas:'2x de R$ 5,00' },
            { id:18, nome:'Base Oil Free', preco:'R$ 15,00', precoNum:15.00, precoAntigo:'R$ 25,00',
              imagens:['base5-1.jpg','base5-2.jpg','base5-3.jpg','base5-4.jpg','base5-5.jpg','base5-6.jpg','base5-7.jpg'],
              descricao:'Base Oil Free desenvolvida especialmente para peles oleosas. Controla a oleosidade por horas sem ressecar.\n\n✔ Livre de óleo\n✔ Controla oleosidade\n✔ Efeito matte\n✔ Não entope poros\n✔ Ideal para pele oleosa e mista',
              categoria:'Base', destaque:false, vendidos:78, parcelas:'3x de R$ 5,00' },
            { id:22, nome:'Base Hipoalergênica', preco:'R$ 15,00', precoNum:15.00, precoAntigo:'R$ 25,00',
              imagens:['base6-1.jpg','base6-2.jpg','base6-3.jpg','base6-4.jpg','base6-5.jpg','base6-6.jpg','base6-7.jpg'],
              descricao:'Base Hipoalergênica formulada especialmente para peles sensíveis. Testada dermatologicamente.\n\n✔ Hipoalergênica\n✔ Testada dermatologicamente\n✔ Ideal para pele sensível\n✔ Sem parabenos\n✔ Fórmula suave',
              categoria:'Base', destaque:false, vendidos:56, parcelas:'3x de R$ 5,00' },
            { id:25, nome:'Base Pó Mineral', preco:'R$ 15,00', precoNum:15.00, precoAntigo:'R$ 25,00',
              imagens:['base7-1.jpg','base7-2.jpg','base7-3.jpg','base7-4.jpg','base7-5.jpg','base7-6.jpg','base7-7.jpg'],
              descricao:'Base em pó mineral com cobertura natural e acabamento aveludado. Perfeita para finalizar a maquiagem.\n\n✔ Pó mineral\n✔ Cobertura natural\n✔ Acabamento aveludado\n✔ Controle de brilho\n✔ Leve e confortável',
              categoria:'Base', destaque:false, vendidos:89, parcelas:'3x de R$ 5,00' },
            { id:28, nome:'Base Cobertura Total', preco:'R$ 15,00', precoNum:15.00, precoAntigo:'R$ 25,00',
              imagens:['base8-1.jpg','base8-2.jpg','base8-3.jpg','base8-4.jpg','base8-5.jpg','base8-6.jpg','base8-7.jpg'],
              descricao:'Base com cobertura total que disfarça manchas, cicatrizes e imperfeições. Acabamento profissional.\n\n✔ Cobertura total\n✔ Alta pigmentação\n✔ Longa duração\n✔ Não transfere\n✔ Acabamento profissional',
              categoria:'Base', destaque:false, vendidos:67, parcelas:'3x de R$ 5,00' },
            { id:2, nome:'Batom Vivaí Cremoso', preco:'R$ 10,00', precoNum:10.00, precoAntigo:'R$ 18,00',
              imagens:['batom1-1.jpg','batom1-2.jpg','batom1-3.jpg','batom1-4.jpg','batom1-5.jpg','batom1-6.jpg','batom1-7.jpg'],
              descricao:'Batom Vivaí Cremoso com textura ultra macia que desliza nos lábios. Alta pigmentação e conforto durante horas.\n\n✔ Textura cremosa\n✔ Alta pigmentação\n✔ Hidrata os lábios\n✔ Longa duração\n✔ Disponível em 6 tons',
              categoria:'Batom', destaque:true, vendidos:215, parcelas:'2x de R$ 5,00' },
            { id:3, nome:'Batom Matte Luxo', preco:'R$ 10,00', precoNum:10.00, precoAntigo:'R$ 18,00',
              imagens:['batom2-1.jpg','batom2-2.jpg','batom2-3.jpg','batom2-4.jpg','batom2-5.jpg','batom2-6.jpg','batom2-7.jpg'],
              descricao:'Batom Matte Luxo com acabamento seco e alta fixação. Cor intensa que dura o dia inteiro.\n\n✔ Acabamento matte\n✔ Altíssima fixação\n✔ Cor intensa\n✔ Não resseca\n✔ Não transfere',
              categoria:'Batom', destaque:true, vendidos:178, parcelas:'2x de R$ 5,00' },
            { id:6, nome:'Batom Vermelho Matte', preco:'R$ 10,00', precoNum:10.00, precoAntigo:null,
              imagens:['batom3-1.jpg','batom3-2.jpg','batom3-3.jpg','batom3-4.jpg','batom3-5.jpg','batom3-6.jpg','batom3-7.jpg'],
              descricao:'O clássico vermelho matte que nunca sai de moda. Cor intensa e marcante para qualquer ocasião.\n\n✔ Vermelho intenso\n✔ Acabamento matte\n✔ Longa duração\n✔ Alta pigmentação\n✔ Não borra',
              categoria:'Batom', destaque:false, vendidos:134, parcelas:'2x de R$ 5,00' },
            { id:9, nome:'Batom Rosa Choque', preco:'R$ 10,00', precoNum:10.00, precoAntigo:null,
              imagens:['batom4-1.jpg','batom4-2.jpg','batom4-3.jpg','batom4-4.jpg','batom4-5.jpg','batom4-6.jpg','batom4-7.jpg'],
              descricao:'Batom rosa choque vibrante para quem ama ousar. Cor marcante e moderna.\n\n✔ Rosa vibrante\n✔ Alta pigmentação\n✔ Acabamento cremoso\n✔ Longa duração\n✔ Moderno e ousado',
              categoria:'Batom', destaque:false, vendidos:156, parcelas:'2x de R$ 5,00' },
            { id:12, nome:'Batom Nude Perfeito', preco:'R$ 10,00', precoNum:10.00, precoAntigo:null,
              imagens:['batom5-1.jpg','batom5-2.jpg','batom5-3.jpg','batom5-4.jpg','batom5-5.jpg','batom5-6.jpg','batom5-7.jpg'],
              descricao:'Batom nude que valoriza qualquer tom de pele. Perfeito para o dia a dia com elegância.\n\n✔ Nude universal\n✔ Acabamento natural\n✔ Hidratante\n✔ Longa duração\n✔ Combina com qualquer look',
              categoria:'Batom', destaque:false, vendidos:203, parcelas:'2x de R$ 5,00' },
            { id:15, nome:'Batom Vinho Escuro', preco:'R$ 10,00', precoNum:10.00, precoAntigo:null,
              imagens:['batom6-1.jpg','batom6-2.jpg','batom6-3.jpg','batom6-4.jpg','batom6-5.jpg','batom6-6.jpg','batom6-7.jpg'],
              descricao:'Batom vinho com acabamento matte para um look sofisticado e marcante.\n\n✔ Cor vinho intensa\n✔ Acabamento matte\n✔ Alta fixação\n✔ Elegante e moderno\n✔ Ideal para festas',
              categoria:'Batom', destaque:false, vendidos:178, parcelas:'2x de R$ 5,00' },
            { id:17, nome:'Batom Laranja Coral', preco:'R$ 10,00', precoNum:10.00, precoAntigo:null,
              imagens:['batom7-1.jpg','batom7-2.jpg','batom7-3.jpg','batom7-4.jpg','batom7-5.jpg','batom7-6.jpg','batom7-7.jpg'],
              descricao:'Batom laranja coral vibrante que traz frescor e juventude ao look.\n\n✔ Coral vibrante\n✔ Alta pigmentação\n✔ Acabamento cremoso\n✔ Ilumina o rosto\n✔ Perfeito para o verão',
              categoria:'Batom', destaque:false, vendidos:134, parcelas:'2x de R$ 5,00' },
            { id:20, nome:'Batom Cereja', preco:'R$ 10,00', precoNum:10.00, precoAntigo:null,
              imagens:['batom8-1.jpg','batom8-2.jpg','batom8-3.jpg','batom8-4.jpg','batom8-5.jpg','batom8-6.jpg','batom8-7.jpg'],
              descricao:'Batom cereja com tom avermelhado intenso e acabamento brilhante.\n\n✔ Cor cereja vibrante\n✔ Acabamento brilhante\n✔ Alta pigmentação\n✔ Longa duração\n✔ Marcante e sensual',
              categoria:'Batom', destaque:false, vendidos:189, parcelas:'2x de R$ 5,00' },
            { id:21, nome:'Batom Amêndoa', preco:'R$ 10,00', precoNum:10.00, precoAntigo:null,
              imagens:['batom9-1.jpg','batom9-2.jpg','batom9-3.jpg','batom9-4.jpg','batom9-5.jpg','batom9-6.jpg','batom9-7.jpg'],
              descricao:'Batom tom amêndoa, perfeito para um look natural e elegante.\n\n✔ Tom amêndoa\n✔ Acabamento natural\n✔ Hidrata os lábios\n✔ Longa duração\n✔ Para o dia a dia',
              categoria:'Batom', destaque:false, vendidos:201, parcelas:'2x de R$ 5,00' },
            { id:24, nome:'Batom Chocolate', preco:'R$ 10,00', precoNum:10.00, precoAntigo:null,
              imagens:['batom10-1.jpg','batom10-2.jpg','batom10-3.jpg','batom10-4.jpg','batom10-5.jpg','batom10-6.jpg','batom10-7.jpg'],
              descricao:'Batom chocolate com tom marrom quente, perfeito para peles morenas e negras.\n\n✔ Tom chocolate\n✔ Alta pigmentação\n✔ Acabamento matte\n✔ Longa duração\n✔ Elegante e sofisticado',
              categoria:'Batom', destaque:false, vendidos:167, parcelas:'2x de R$ 5,00' },
            { id:27, nome:'Batom Roxo Intenso', preco:'R$ 10,00', precoNum:10.00, precoAntigo:null,
              imagens:['batom11-1.jpg','batom11-2.jpg','batom11-3.jpg','batom11-4.jpg','batom11-5.jpg','batom11-6.jpg','batom11-7.jpg'],
              descricao:'Batom roxo intenso para quem gosta de ousar e marcar presença.\n\n✔ Roxo intenso\n✔ Alta pigmentação\n✔ Acabamento matte\n✔ Longa duração\n✔ Para looks ousados',
              categoria:'Batom', destaque:false, vendidos:145, parcelas:'2x de R$ 5,00' },
            { id:30, nome:'Batom Glossy Pink', preco:'R$ 10,00', precoNum:10.00, precoAntigo:null,
              imagens:['batom12-1.jpg','batom12-2.jpg','batom12-3.jpg','batom12-4.jpg','batom12-5.jpg','batom12-6.jpg','batom12-7.jpg'],
              descricao:'Batom rosa glossy que combina o conforto de um bálsamo com o brilho de um gloss.\n\n✔ Rosa com brilho\n✔ Hidratante\n✔ Acabamento glossy\n✔ Longa duração\n✔ Aparência saudável',
              categoria:'Batom', destaque:false, vendidos:198, parcelas:'2x de R$ 5,00' },
            { id:4, nome:'Gloss Diamond', preco:'R$ 10,00', precoNum:10.00, precoAntigo:'R$ 18,00',
              imagens:['gloss1-1.jpg','gloss1-2.jpg','gloss1-3.jpg','gloss1-4.jpg','gloss1-5.jpg','gloss1-6.jpg','gloss1-7.jpg'],
              descricao:'Gloss Diamond com partículas brilhantes que dão aquele efeito de lábios molhados e volumosos.\n\n✔ Brilho intenso\n✔ Efeito volumoso\n✔ Textura não pegajosa\n✔ Hidratante\n✔ Aparência de lábios de cristal',
              categoria:'Gloss', destaque:true, vendidos:456, parcelas:'2x de R$ 5,00' },
            { id:7, nome:'Gloss Cintilante', preco:'R$ 10,00', precoNum:10.00, precoAntigo:'R$ 18,00',
              imagens:['gloss2-1.jpg','gloss2-2.jpg','gloss2-3.jpg','gloss2-4.jpg','gloss2-5.jpg','gloss2-6.jpg','gloss2-7.jpg'],
              descricao:'Gloss cintilante com brilho delicado, perfeito para o dia a dia.\n\n✔ Cintilância suave\n✔ Textura leve\n✔ Não pegajoso\n✔ Hidratante\n✔ Efeito natural',
              categoria:'Gloss', destaque:false, vendidos:267, parcelas:'2x de R$ 5,00' },
            { id:11, nome:'Gloss Vermelho Intenso', preco:'R$ 10,00', precoNum:10.00, precoAntigo:null,
              imagens:['gloss3-1.jpg','gloss3-2.jpg','gloss3-3.jpg','gloss3-4.jpg','gloss3-5.jpg','gloss3-6.jpg','gloss3-7.jpg'],
              descricao:'Gloss vermelho com alto brilho e cor intensa. Marca presença em qualquer look.\n\n✔ Vermelho vibrante\n✔ Alto brilho\n✔ Efeito molhado\n✔ Longa duração\n✔ Marcante e ousado',
              categoria:'Gloss', destaque:false, vendidos:89, parcelas:'2x de R$ 5,00' },
            { id:14, nome:'Gloss Dourado', preco:'R$ 10,00', precoNum:10.00, precoAntigo:'R$ 18,00',
              imagens:['gloss4-1.jpg','gloss4-2.jpg','gloss4-3.jpg','gloss4-4.jpg','gloss4-5.jpg','gloss4-6.jpg','gloss4-7.jpg'],
              descricao:'Gloss dourado com partículas brilhantes que iluminam os lábios.\n\n✔ Dourado brilhante\n✔ Efeito iluminado\n✔ Textura confortável\n✔ Brilho metálico\n✔ Para ocasiões especiais',
              categoria:'Gloss', destaque:false, vendidos:145, parcelas:'2x de R$ 5,00' },
            { id:19, nome:'Gloss Lilás', preco:'R$ 10,00', precoNum:10.00, precoAntigo:'R$ 18,00',
              imagens:['gloss5-1.jpg','gloss5-2.jpg','gloss5-3.jpg','gloss5-4.jpg','gloss5-5.jpg','gloss5-6.jpg','gloss5-7.jpg'],
              descricao:'Gloss lilás com brilho delicado e moderno. Perfeito para looks criativos.\n\n✔ Lilás delicado\n✔ Brilho sutil\n✔ Textura leve\n✔ Hidratante\n✔ Moderno e único',
              categoria:'Gloss', destaque:false, vendidos:156, parcelas:'2x de R$ 5,00' },
            { id:23, nome:'Gloss Pink', preco:'R$ 10,00', precoNum:10.00, precoAntigo:null,
              imagens:['gloss6-1.jpg','gloss6-2.jpg','gloss6-3.jpg','gloss6-4.jpg','gloss6-5.jpg','gloss6-6.jpg','gloss6-7.jpg'],
              descricao:'Gloss rosa com brilho encantador e textura confortável.\n\n✔ Rosa vibrante\n✔ Alto brilho\n✔ Não pegajoso\n✔ Longa duração\n✔ Favorito entre as clientes',
              categoria:'Gloss', destaque:false, vendidos:134, parcelas:'2x de R$ 5,00' },
            { id:26, nome:'Gloss Transparente', preco:'R$ 10,00', precoNum:10.00, precoAntigo:null,
              imagens:['gloss7-1.jpg','gloss7-2.jpg','gloss7-3.jpg','gloss7-4.jpg','gloss7-5.jpg','gloss7-6.jpg','gloss7-7.jpg'],
              descricao:'O clássico gloss transparente que combina com qualquer batom. Efeito de lábios molhados.\n\n✔ Transparente\n✔ Efeito molhado\n✔ Combina com qualquer cor\n✔ Hidratante\n✔ Versátil',
              categoria:'Gloss', destaque:false, vendidos:223, parcelas:'2x de R$ 5,00' },
            { id:29, nome:'Gloss Rosé', preco:'R$ 10,00', precoNum:10.00, precoAntigo:'R$ 18,00',
              imagens:['gloss8-1.jpg','gloss8-2.jpg','gloss8-3.jpg','gloss8-4.jpg','gloss8-5.jpg','gloss8-6.jpg','gloss8-7.jpg'],
              descricao:'Gloss rosé com tom sofisticado e brilho elegante.\n\n✔ Tom rosé\n✔ Brilho sofisticado\n✔ Textura confortável\n✔ Longa duração\n✔ Elegante e delicado',
              categoria:'Gloss', destaque:false, vendidos:178, parcelas:'2x de R$ 5,00' }
        ];

        let favoritos = [];
        let carrinho = [];
        let notificacoes = [];
        let notifId = 0;
        let notaSelecionada = 0;
        let fotoTemporaria = null;
        let produtoAtualDetalhes = null;
        let corSelecionadaDetalhes = '';

        let avaliacoes = [
            { nome:'Maria Silva', produto:'Base Matte Premium', nota:5, texto:'Produto maravilhoso! Minha pele ficou perfeita.', data:'10/01/2026', curtidas:12 },
            { nome:'Fernanda Lima', produto:'Batom Matte Luxo', nota:5, texto:'Amei a cor e a durabilidade. Super recomendo!', data:'08/01/2026', curtidas:8 },
            { nome:'Camila Rocha', produto:'Gloss Diamond', nota:4, texto:'Muito bonito, brilho incrível.', data:'05/01/2026', curtidas:4 },
            { nome:'Ana Paula', produto:'Base Iluminadora', nota:5, texto:'Cobertura perfeita e iluminada.', data:'03/01/2026', curtidas:15 }
        ];

        let feedbacks = [
            { nome:'Cliente 1', texto:'Loja incrível, produtos de qualidade e entrega rápida!' },
            { nome:'Cliente 2', texto:'Atendimento excelente, tirei todas minhas dúvidas.' }
        ];

        // ================================================================
        // 🎠 RENDERIZAR CARROSSEL
        // ================================================================
        function renderizarCarrossel() {
            const container = document.getElementById('bannerSlides');
            if (!container) return;
            container.innerHTML = '';

            carrosselSlides.forEach(slide => {
                let acaoJS = '';
                if (slide.acao === 'produtos') acaoJS = "navegar('produtos')";
                // AQUI É ONDE O CARROSSEL CHAMA O AGENDAMENTO
                else if (slide.acao === 'agendar') acaoJS = "window.location.href='agendamento.html'";
                else if (slide.acao === 'inicio') acaoJS = "navegar('inicio')";
                else acaoJS = "navegar('produtos')";

                const div = document.createElement('div');
                div.className = 'banner-slide';
                div.innerHTML = `
                    <div class="slide-content">
                        <div class="slide-text">
                            <h2>${slide.titulo} <span>${slide.destaque}</span></h2>
                            <p>${slide.subtitulo}</p>
                            <button onclick="${acaoJS}">
                                <i class="fa-regular ${slide.iconeBotao}"></i> ${slide.textoBotao}
                            </button>
                        </div>
                        <div class="slide-image">
                            <i class="fa-regular ${slide.iconeSlide}"></i>
                        </div>
                    </div>
                `;
                container.appendChild(div);
            });
        }

        // ================================================================
        // RENDERIZAÇÕES GERAIS
        // ================================================================
        function renderizarProdutos(produtosArray, containerId) {
            const container = document.getElementById(containerId);
            if (!container) return;
            container.innerHTML = '';
            produtosArray.forEach(p => {
                const isFav = favoritos.some(f => f.id === p.id);
                const card = document.createElement('div');
                card.className = 'card';
                card.setAttribute('data-id', p.id);
                card.setAttribute('data-categoria', p.categoria);
                const temPromo = p.precoAntigo !== null;
                const imagemCapa = (p.imagens && p.imagens.length > 0) ? p.imagens[0] : (p.imagem || 'sem-foto.jpg');
                card.innerHTML = `
                    <div class="card-image" onclick="abrirDetalhesProduto(${p.id})" style="cursor:pointer;">
                        <img src="${imagemCapa}" alt="${p.nome}" onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=%22http://www.w3.org/2000/svg%22 width=%22300%22 height=%22300%22><rect fill=%22%23141414%22 width=%22300%22 height=%22300%22/><text x=%2250%25%22 y=%2250%25%22 fill=%22%23FF1493%22 font-size=%2218%22 text-anchor=%22middle%22 dy=%22.3em%22>TC Beauty</text></svg>'" />
                        <button class="favorito ${isFav ? 'ativo' : ''}" onclick="event.stopPropagation(); toggleFavorito(${p.id})">
                            <i class="${isFav ? 'fa-solid' : 'fa-regular'} fa-heart"></i>
                        </button>
                        ${temPromo ? `<span class="promo-tag">Promoção</span>` : ''}
                    </div>
                    <div class="info">
                        <div class="nome" onclick="abrirDetalhesProduto(${p.id})" style="cursor:pointer;">${p.nome}</div>
                        <div class="categoria-tag">${p.categoria}</div>
                        <div class="preco">
                            ${p.preco}
                            ${p.precoAntigo ? `<span class="preco-antigo">${p.precoAntigo}</span>` : ''}
                        </div>
                        <div class="parcelamento">${p.parcelas} sem juros</div>
                        <div class="avaliacao">
                            <span class="estrelas">★★★★★</span>
                            <span class="qtd">(${p.vendidos} vendidos)</span>
                        </div>
                        <div class="botoes-acoes">
                            <button class="btn btn-comprar" onclick="abrirDetalhesProduto(${p.id})">
                                <i class="fa-regular fa-bag-shopping"></i> Comprar
                            </button>
                            <button class="btn btn-carrinho" onclick="adicionarAoCarrinho(${p.id})">
                                <i class="fa-solid fa-cart-plus"></i>
                            </button>
                        </div>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function renderizarAvaliacoes() {
            const container = document.getElementById('avaliacoesGrid');
            if (!container) return;
            container.innerHTML = '';
            avaliacoes.forEach((a, index) => {
                const estrelas = '★'.repeat(a.nota) + '☆'.repeat(5 - a.nota);
                const div = document.createElement('div');
                div.className = 'avaliacao-card';
                div.innerHTML = `
                    <div class="avaliacao-header">
                        <span class="nome">${a.nome}</span>
                        <span class="estrelas">${estrelas}</span>
                        <span class="data">${a.data}</span>
                    </div>
                    <p><strong style="color:#888;">${a.produto}</strong> - ${a.texto}</p>
                    <div class="curtir" onclick="curtirAvaliacao(${index})">
                        <i class="fa-regular fa-heart"></i> <span>${a.curtidas}</span> curtidas
                    </div>
                `;
                container.appendChild(div);
            });
        }

        function renderizarFeedbacks() {
            const container = document.getElementById('feedbacksLista');
            if (!container) return;
            container.innerHTML = '';
            feedbacks.forEach((f, index) => {
                const div = document.createElement('div');
                div.className = 'feedback-item';
                div.innerHTML = `
                    <div class="feedback-nome">${f.nome}</div>
                    <div class="feedback-texto">${f.texto}</div>
                    <button class="feedback-responder" onclick="responderFeedback(${index})">
                        <i class="fa-regular fa-reply"></i> Responder
                    </button>
                `;
                container.appendChild(div);
            });
        }

        function renderizarFavoritos() {
            const container = document.getElementById('gridFavoritos');
            const vazio = document.getElementById('favoritosVazio');
            if (!container) return;
            if (favoritos.length === 0) {
                container.innerHTML = '';
                vazio.style.display = 'block';
                return;
            }
            vazio.style.display = 'none';
            renderizarProdutos(favoritos, 'gridFavoritos');
        }

        function renderizarCarrinho() {
            const container = document.getElementById('carrinhoItens');
            const vazio = document.getElementById('carrinhoVazio');
            const resumo = document.getElementById('carrinhoResumo');
            const badge = document.getElementById('carrinhoBadge');
            badge.textContent = carrinho.reduce((acc, item) => acc + item.qtd, 0);

            if (carrinho.length === 0) {
                container.innerHTML = '';
                vazio.style.display = 'block';
                resumo.style.display = 'none';
                return;
            }
            vazio.style.display = 'none';
            resumo.style.display = 'block';
            container.innerHTML = '';
            let subtotal = 0;
            carrinho.forEach((item, index) => {
                const p = produtos.find(prod => prod.id === item.id);
                if (!p) return;
                const totalItem = p.precoNum * item.qtd;
                subtotal += totalItem;
                const imgCarrinho = (p.imagens && p.imagens.length > 0) ? p.imagens[0] : (p.imagem || '');
                const div = document.createElement('div');
                div.className = 'carrinho-item';
                div.innerHTML = `
                    <img src="${imgCarrinho}" alt="${p.nome}" onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=%22http://www.w3.org/2000/svg%22 width=%22100%22 height=%22100%22><rect fill=%22%23141414%22 width=%22100%22 height=%22100%22/><text x=%2250%25%22 y=%2250%25%22 fill=%22%23FF1493%22 font-size=%2210%22 text-anchor=%22middle%22 dy=%22.3em%22>TC</text></svg>'" />
                    <div class="info">
                        <div class="nome">${p.nome}</div>
                        <div class="preco">${p.preco}</div>
                    </div>
                    <div class="qtd-control">
                        <button onclick="alterarQtdCarrinho(${index}, -1)">−</button>
                        <span>${item.qtd}</span>
                        <button onclick="alterarQtdCarrinho(${index}, 1)">+</button>
                    </div>
                    <button class="remover" onclick="removerDoCarrinho(${index})"><i class="fa-regular fa-trash-can"></i></button>
                `;
                container.appendChild(div);
            });
            const frete = 4.00;
            const total = subtotal + frete;
            document.getElementById('carrinhoSubtotal').textContent = `R$ ${subtotal.toFixed(2).replace('.', ',')}`;
            document.getElementById('carrinhoFrete').textContent = `R$ ${frete.toFixed(2).replace('.', ',')}`;
            document.getElementById('carrinhoTotal').textContent = `R$ ${total.toFixed(2).replace('.', ',')}`;
        }

        function renderizarNotificacoes() {
            const container = document.getElementById('notificacoesLista');
            const badge = document.getElementById('notifBadge');
            if (!container) return;
            const naoLidas = notificacoes.filter(n => !n.lida).length;
            badge.textContent = naoLidas;
            if (notificacoes.length === 0) {
                container.innerHTML = `
                    <div style="text-align:center;padding:40px;color:#666;">
                        <i class="fa-regular fa-bell-slash" style="font-size:40px;color:#333;display:block;margin-bottom:12px;"></i>
                        <p>Nenhuma notificação ainda.</p>
                    </div>`;
                return;
            }
            container.innerHTML = '';
            notificacoes.slice().reverse().forEach((n, idx) => {
                const realIndex = notificacoes.length - 1 - idx;
                const div = document.createElement('div');
                div.className = 'notif-item';
                div.style.opacity = n.lida ? '0.6' : '1';
                div.innerHTML = `
                    <div class="notif-icon"><i class="${n.icone || 'fa-regular fa-bell'}"></i></div>
                    <div class="notif-conteudo">
                        <div class="notif-titulo">${n.titulo}</div>
                        <div class="notif-texto">${n.texto}</div>
                        <div class="notif-data">${n.data}</div>
                    </div>
                    ${!n.lida ? `<button class="notif-lida" onclick="marcarNotificacaoLida(${realIndex})">Marcar como lida</button>` : ''}
                `;
                container.appendChild(div);
            });
        }

        function renderizarCategoriasFull() {
            const container = document.getElementById('categoriasGridFull');
            if (!container) return;
            const cats = ['Batom','Base','Gloss','Skincare','Perfumes','Acessórios','Promoções','Novidades'];
            const icons = ['fa-regular fa-palette','fa-regular fa-droplet','fa-regular fa-flower','fa-regular fa-wand-magic-sparkles','fa-regular fa-hand','fa-regular fa-ring','fa-regular fa-tag','fa-regular fa-sparkles'];
            container.innerHTML = '';
            cats.forEach((cat, i) => {
                const div = document.createElement('div');
                div.className = 'categoria-item';
                div.setAttribute('data-categoria', cat);
                div.innerHTML = `<i class="${icons[i]}"></i><span>${cat}</span>`;
                div.addEventListener('click', function() { filtrarPorCategoria(cat); });
                container.appendChild(div);
            });
        }

        // ================================================================
        // PÁGINA DE DETALHES - LAYOUT VERTICAL
        // ================================================================
        function abrirDetalhesProduto(id) {
            const p = produtos.find(prod => prod.id === id);
            if (!p) return;
            produtoAtualDetalhes = p;
            corSelecionadaDetalhes = 'Tom 01';

            const container = document.getElementById('produtoDetalhes');
            const temPromo = p.precoAntigo !== null;

            let imagensProduto = [];
            if (p.imagens && Array.isArray(p.imagens)) {
                imagensProduto = p.imagens;
            } else if (p.imagem) {
                imagensProduto = [p.imagem];
            }
            if (imagensProduto.length === 0) imagensProduto = ['sem-foto.jpg'];
            imagensProduto = imagensProduto.slice(0, 7);

            const imagemPrincipal = imagensProduto[0];

            const miniaturasHTML = imagensProduto.map((img, i) =>
                `<img src="${img}" class="${i === 0 ? 'ativa' : ''}" 
                      onclick="trocarImagemPrincipal(this, '${img}')" 
                      onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=%22http://www.w3.org/2000/svg%22 width=%2280%22 height=%2280%22><rect fill=%22%23141414%22 width=%2280%22 height=%2280%22/><text x=%2250%25%22 y=%2250%25%22 fill=%22%23FF1493%22 font-size=%2210%22 text-anchor=%22middle%22 dy=%22.3em%22>TC</text></svg>'" />`
            ).join('');

            const coresDisponiveis = ['Tom 01', 'Tom 02', 'Tom 03', 'Tom 04', 'Tom 05', 'Tom 06'];
            const coresHTML = coresDisponiveis.map((cor, i) =>
                `<button class="cor-btn ${i === 0 ? 'selecionada' : ''}" onclick="selecionarCor(this, '${cor}')">${cor}</button>`
            ).join('');

            const descricaoProduto = p.descricao || 'Produto premium da linha TC Beauty, desenvolvido com ingredientes de alta qualidade e testado dermatologicamente. Ideal para o dia a dia, oferece longa duração, cobertura perfeita e acabamento profissional. Um item indispensável na sua nécessaire!';

            container.innerHTML = `
                <div class="imagem-principal-container">
                    <img id="imagemPrincipalProduto" src="${imagemPrincipal}" alt="${p.nome}" 
                         onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=%22http://www.w3.org/2000/svg%22 width=%22400%22 height=%22400%22><rect fill=%22%23141414%22 width=%22400%22 height=%22400%22/><text x=%2250%25%22 y=%2250%25%22 fill=%22%23FF1493%22 font-size=%2224%22 text-anchor=%22middle%22 dy=%22.3em%22>TC Beauty</text></svg>'" />
                </div>

                <div class="miniaturas-container">
                    ${miniaturasHTML}
                </div>

                <div class="produto-detalhes-info">
                    <div class="breadcrumb">
                        <i class="fa-solid fa-house"></i>
                        <span>Início</span>
                        <i class="fa-solid fa-chevron-right" style="font-size:9px;"></i>
                        <span>${p.categoria}</span>
                        <i class="fa-solid fa-chevron-right" style="font-size:9px;"></i>
                        <span>${p.nome}</span>
                    </div>

                    <h1 class="nome-produto">${p.nome}</h1>

                    <div class="avaliacao-linha">
                        <span class="estrelas">★★★★★</span>
                        <span class="vendidos">(${p.vendidos} vendidos)</span>
                    </div>

                    <div class="preco-bloco">
                        ${temPromo ? `<div class="preco-antigo-grande">${p.precoAntigo}</div>` : ''}
                        <div class="preco-grande">
                            ${p.preco}
                            ${temPromo ? `<span class="desconto-tag">Promoção</span>` : ''}
                        </div>
                        <div class="parcelas">ou <strong>${p.parcelas}</strong> sem juros no cartão</div>
                    </div>

                    <div>
                        <div class="titulo-secao"><i class="fa-solid fa-align-left"></i> Descrição do produto</div>
                        <p class="descricao-produto">${descricaoProduto}</p>
                    </div>

                    <div>
                        <div class="titulo-secao"><i class="fa-solid fa-palette"></i> Cor disponível</div>
                        <div class="cores-opcoes" id="coresOpcoes">
                            ${coresHTML}
                        </div>
                    </div>

                    <div class="acoes">
                        <button class="btn-principal" onclick="comprarDetalhes()">
                            <i class="fa-brands fa-whatsapp"></i> Comprar pelo WhatsApp
                        </button>
                        <button class="btn-secundario" onclick="adicionarDetalhesAoCarrinho()">
                            <i class="fa-solid fa-cart-plus"></i> Adicionar ao Carrinho
                        </button>
                    </div>

                    <div class="info-extras">
                        <div class="item-extra">
                            <i class="fa-solid fa-truck-fast"></i>
                            <span>Taxa de entrega R$ 4,00</span>
                        </div>
                        <div class="item-extra">
                            <i class="fa-solid fa-shield-halved"></i>
                            <span>Produto original</span>
                        </div>
                        <div class="item-extra">
                            <i class="fa-solid fa-star"></i>
                            <span>Qualidade premium</span>
                        </div>
                    </div>
                </div>
            `;

            navegar('produto');
        }

        function trocarImagemPrincipal(el, src) {
            document.getElementById('imagemPrincipalProduto').src = src;
            document.querySelectorAll('.produto-detalhes .miniaturas-container img').forEach(img => {
                img.classList.remove('ativa');
            });
            el.classList.add('ativa');
        }

        function selecionarCor(el, cor) {
            corSelecionadaDetalhes = cor;
            document.querySelectorAll('#coresOpcoes .cor-btn').forEach(btn => {
                btn.classList.remove('selecionada');
            });
            el.classList.add('selecionada');
        }

        function comprarDetalhes() {
            if (!produtoAtualDetalhes) return;
            const msg = `Olá! Gostaria de comprar:\n\n📦 *Produto:* ${produtoAtualDetalhes.nome}\n💰 *Preço:* ${produtoAtualDetalhes.preco}\n🎨 *Cor:* ${corSelecionadaDetalhes}\n\nAguardo a confirmação! 💕`;
            window.open('https://wa.me/5513992084636?text=' + encodeURIComponent(msg), '_blank');
            toast('📨 Mensagem enviada!', 'Sua solicitação foi enviada para o WhatsApp.');
        }

        function adicionarDetalhesAoCarrinho() {
            if (!produtoAtualDetalhes) return;
            adicionarAoCarrinho(produtoAtualDetalhes.id);
        }

        // ================================================================
        // AÇÕES
        // ================================================================
        function toggleFavorito(id) {
            const p = produtos.find(prod => prod.id === id);
            if (!p) return;
            const idx = favoritos.findIndex(f => f.id === id);
            if (idx === -1) {
                favoritos.push(p);
                toast('❤️ Adicionado aos favoritos!', `${p.nome} foi salvo.`);
                adicionarNotificacao('❤️ Favorito adicionado', `${p.nome} foi adicionado aos seus favoritos.`, 'fa-regular fa-heart');
            } else {
                favoritos.splice(idx, 1);
                toast('💔 Removido dos favoritos', `${p.nome} foi removido.`);
            }
            renderizarFavoritos();
            renderizarProdutos(produtos.filter(p => p.destaque), 'gridDestaques');
            renderizarProdutos(produtos, 'gridTodosProdutos');
        }

        function adicionarAoCarrinho(id) {
            const p = produtos.find(prod => prod.id === id);
            if (!p) return;
            const existente = carrinho.find(item => item.id === id);
            if (existente) existente.qtd++;
            else carrinho.push({ id: p.id, qtd: 1 });
            renderizarCarrinho();
            toast('🛒 Adicionado ao carrinho!', `${p.nome} foi adicionado.`);
            adicionarNotificacao('🛒 Carrinho atualizado', `${p.nome} foi adicionado ao carrinho.`, 'fa-solid fa-cart-plus');
        }

        function alterarQtdCarrinho(index, delta) {
            if (carrinho[index]) {
                carrinho[index].qtd += delta;
                if (carrinho[index].qtd <= 0) carrinho.splice(index, 1);
                renderizarCarrinho();
            }
        }

        function removerDoCarrinho(index) {
            const item = carrinho[index];
            const p = produtos.find(prod => prod.id === item.id);
            carrinho.splice(index, 1);
            renderizarCarrinho();
            if (p) toast('🗑️ Removido', `${p.nome} foi removido do carrinho.`);
        }

        function marcarNotificacaoLida(index) {
            if (notificacoes[index]) {
                notificacoes[index].lida = true;
                renderizarNotificacoes();
            }
        }

        function adicionarNotificacao(titulo, texto, icone = 'fa-regular fa-bell') {
            const data = new Date().toLocaleDateString('pt-BR') + ' ' + new Date().toLocaleTimeString('pt-BR', { hour:'2-digit', minute:'2-digit' });
            notificacoes.push({ id: notifId++, titulo, texto, data, lida: false, icone });
            renderizarNotificacoes();
        }

        function curtirAvaliacao(index) {
            avaliacoes[index].curtidas++;
            renderizarAvaliacoes();
            toast('👍 Curtido!', 'Você curtiu essa avaliação.');
        }

        function responderFeedback(index) {
            const resposta = prompt('Digite sua resposta para o feedback:');
            if (resposta) {
                const nome = feedbacks[index].nome;
                feedbacks.splice(index + 1, 0, { nome: '💬 TC Beauty', texto: `Resposta para ${nome}: ${resposta}` });
                renderizarFeedbacks();
                toast('📨 Resposta enviada!', 'O cliente verá sua resposta em breve.');
                adicionarNotificacao('📨 Resposta enviada', `Você respondeu ao feedback de ${nome}`, 'fa-regular fa-reply');
            }
        }

        function filtrarPorCategoria(categoria) {
            navegar('produtos');
            setTimeout(() => {
                const cards = document.querySelectorAll('#gridTodosProdutos .card');
                let encontrou = false;
                cards.forEach(card => {
                    const tag = card.getAttribute('data-categoria');
                    if (tag === categoria) { card.style.display = 'block'; encontrou = true; }
                    else { card.style.display = 'none'; }
                });
                if (!encontrou) toast('📂 Categoria vazia', 'Nenhum produto nesta categoria.');
                else toast('📂 Categoria filtrada', `Mostrando produtos da categoria ${categoria}.`);
            }, 100);
        }

        function finalizarCompra() {
            if (carrinho.length === 0) { toast('⚠️ Carrinho vazio', 'Adicione produtos antes de finalizar.'); return; }
            let mensagem = '🛍️ *NOVO PEDIDO - TC Beauty*%0A%0A';
            let subtotal = 0;
            carrinho.forEach(item => {
                const p = produtos.find(prod => prod.id === item.id);
                if (p) {
                    const totalItem = p.precoNum * item.qtd;
                    subtotal += totalItem;
                    mensagem += `📦 ${p.nome}%0A`;
                    mensagem += ` Quantidade: ${item.qtd}%0A`;
                    mensagem += ` Valor: ${p.preco}%0A`;
                    mensagem += ` Subtotal: R$ ${totalItem.toFixed(2).replace('.', ',')}%0A%0A`;
                }
            });
            const frete = 4.00;
            const total = subtotal + frete;
            mensagem += `%0A📦 *Taxa de entrega:* R$ ${frete.toFixed(2).replace('.', ',')}%0A`;
            mensagem += `💰 *TOTAL DO PEDIDO:* R$ ${total.toFixed(2).replace('.', ',')}%0A%0A`;

            const cliente = JSON.parse(localStorage.getItem('tcBeautyCliente') || 'null');
            if (cliente) {
                mensagem += `📋 *Dados do cliente:*%0A`;
                mensagem += ` Nome: ${cliente.nome}%0A`;
                mensagem += ` E-mail: ${cliente.email}%0A`;
                mensagem += ` Telefone: ${cliente.telefone}%0A%0A`;
            } else {
                mensagem += `📋 *Dados do cliente:*%0A Nome: Cliente TC Beauty%0A Telefone: (13) 99208-4636%0A%0A`;
            }
            mensagem += `✅ Aguardo a confirmação do pedido!`;
            window.open('https://wa.me/5513992084636?text=' + mensagem, '_blank');
            carrinho = [];
            renderizarCarrinho();
            toast('📨 Pedido enviado!', 'Sua mensagem foi enviada para nosso WhatsApp.');
            adicionarNotificacao('📨 Pedido enviado', 'Seu pedido foi enviado para o WhatsApp da loja.', 'fa-regular fa-check-circle');
        }

        // ================================================================
        // SISTEMA DE CONTA
        // ================================================================
        const CHAVE_CLIENTE = 'tcBeautyCliente';

        function previewFoto(event) {
            const file = event.target.files[0];
            if (!file) return;
            if (file.size > 2 * 1024 * 1024) {
                toast('⚠️ Foto muito grande', 'Escolha uma imagem de até 2MB.');
                return;
            }
            const reader = new FileReader();
            reader.onload = function(e) {
                fotoTemporaria = e.target.result;
                document.getElementById('avatarPreview').src = fotoTemporaria;
                document.getElementById('avatarPreview').style.display = 'block';
                document.getElementById('avatarIcone').style.display = 'none';
            };
            reader.readAsDataURL(file);
        }

        function verificarConta() {
            const cliente = JSON.parse(localStorage.getItem(CHAVE_CLIENTE) || 'null');
            const telaCadastro = document.getElementById('contaCadastro');
            const telaLogado = document.getElementById('contaLogado');

            if (cliente) {
                telaCadastro.style.display = 'none';
                telaLogado.style.display = 'block';
                document.getElementById('contaNome').textContent = cliente.nome;
                document.getElementById('contaEmail').textContent = cliente.email;
                document.getElementById('contaTelefone').textContent = cliente.telefone;
                document.getElementById('contaData').textContent = cliente.dataMembro;

                const avatarLogadoPreview = document.getElementById('avatarLogadoPreview');
                const avatarLogadoIcone = document.getElementById('avatarLogadoIcone');
                if (cliente.foto) {
                    avatarLogadoPreview.src = cliente.foto;
                    avatarLogadoPreview.style.display = 'block';
                    avatarLogadoIcone.style.display = 'none';
                } else {
                    avatarLogadoPreview.style.display = 'none';
                    avatarLogadoIcone.style.display = 'block';
                }
            } else {
                telaCadastro.style.display = 'block';
                telaLogado.style.display = 'none';
                fotoTemporaria = null;
                document.getElementById('avatarPreview').style.display = 'none';
                document.getElementById('avatarIcone').style.display = 'block';
            }
        }

        function cadastrarCliente() {
            const nome = document.getElementById('cadNome').value.trim();
            const email = document.getElementById('cadEmail').value.trim();
            const telefone = document.getElementById('cadTelefone').value.trim();

            if (!nome || !email || !telefone) {
                toast('⚠️ Atenção', 'Preencha todos os campos para se cadastrar.');
                return;
            }
            if (!email.includes('@') || !email.includes('.')) {
                toast('⚠️ E-mail inválido', 'Digite um e-mail válido.');
                return;
            }

            const emailJaUsado = localStorage.getItem('tcBeautyEmail_' + email);
            if (emailJaUsado) {
                toast('⚠️ E-mail já cadastrado', 'Use outro e-mail ou faça login.');
                return;
            }

            const hoje = new Date();
            const dataFormatada = hoje.toLocaleDateString('pt-BR', {
                day: '2-digit', month: 'long', year: 'numeric'
            });

            const cliente = {
                nome: nome, email: email, telefone: telefone,
                dataMembro: dataFormatada, dataCadastro: hoje.toISOString(),
                foto: fotoTemporaria
            };

            localStorage.setItem(CHAVE_CLIENTE, JSON.stringify(cliente));
            localStorage.setItem('tcBeautyEmail_' + email, 'true');

            toast('🎉 Cadastro realizado!', `Bem-vinda, ${nome.split(' ')[0]}!`);
            adicionarNotificacao('🎉 Conta criada', `Sua conta foi criada em ${dataFormatada}.`, 'fa-regular fa-user');

            document.getElementById('cadNome').value = '';
            document.getElementById('cadEmail').value = '';
            document.getElementById('cadTelefone').value = '';
            fotoTemporaria = null;

            verificarConta();
        }

        function trocarFotoLogado() {
            document.getElementById('inputFotoLogado').click();
        }

        function trocarFoto(event) {
            const file = event.target.files[0];
            if (!file) return;
            if (file.size > 2 * 1024 * 1024) {
                toast('⚠️ Foto muito grande', 'Escolha uma imagem de até 2MB.');
                return;
            }
            const reader = new FileReader();
            reader.onload = function(e) {
                const cliente = JSON.parse(localStorage.getItem(CHAVE_CLIENTE) || 'null');
                if (cliente) {
                    cliente.foto = e.target.result;
                    localStorage.setItem(CHAVE_CLIENTE, JSON.stringify(cliente));
                    verificarConta();
                    toast('📸 Foto atualizada!', 'Sua nova foto foi salva.');
                }
            };
            reader.readAsDataURL(file);
        }

        function sairConta() {
            if (confirm('Tem certeza que deseja sair da sua conta?')) {
                localStorage.removeItem(CHAVE_CLIENTE);
                toast('👋 Até logo!', 'Você saiu da sua conta.');
                verificarConta();
            }
        }

        // ================================================================
        // NAVEGAÇÃO
        // ================================================================
        function navegar(page) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
            const target = document.getElementById('page-' + page);
            if (target) target.classList.add('active');
            document.querySelectorAll('.menu-btn').forEach(btn => {
                btn.classList.toggle('active', btn.getAttribute('data-page') === page);
            });
            window.scrollTo({ top: 0, behavior: 'smooth' });
            if (page === 'favoritos') renderizarFavoritos();
            if (page === 'carrinho') renderizarCarrinho();
            if (page === 'notificacoes') renderizarNotificacoes();
            if (page === 'categorias') renderizarCategoriasFull();
            if (page === 'conta') verificarConta();
            if (page === 'avaliacoes') renderizarAvaliacoes();
        }

        // ================================================================
        // BANNER
        // ================================================================
        let bannerIndex = 0;
        let totalSlides = 0;

        function moverBanner(dir) {
            if (totalSlides === 0) return;
            bannerIndex += dir;
            if (bannerIndex < 0) bannerIndex = totalSlides - 1;
            if (bannerIndex >= totalSlides) bannerIndex = 0;
            atualizarBanner();
        }

        function atualizarBanner() {
            const slides = document.getElementById('bannerSlides');
            if (!slides) return;
            slides.style.transform = `translateX(-${bannerIndex * 100}%)`;
            document.querySelectorAll('#bannerDots span').forEach((dot, i) => {
                dot.classList.toggle('active', i === bannerIndex);
            });
        }

        function initBanner() {
            renderizarCarrossel();
            totalSlides = carrosselSlides.length;
            const dotsContainer = document.getElementById('bannerDots');
            dotsContainer.innerHTML = '';
            for (let i = 0; i < totalSlides; i++) {
                const dot = document.createElement('span');
                dot.onclick = () => { bannerIndex = i; atualizarBanner(); };
                dotsContainer.appendChild(dot);
            }
            atualizarBanner();
            setInterval(() => moverBanner(1), 6000);
        }

        // ================================================================
        // TOAST
        // ================================================================
        function toast(titulo, texto) {
            const el = document.getElementById('toast');
            document.getElementById('toastTitulo').textContent = titulo;
            document.getElementById('toastTexto').textContent = texto;
            el.classList.add('mostrar');
            clearTimeout(el._timeout);
            el._timeout = setTimeout(() => el.classList.remove('mostrar'), 3500);
        }

        // ================================================================
        // MODAL
        // ================================================================
        let produtoSelecionado = { nome:'', preco:'' };

        function abrirModal(nome, preco) {
            produtoSelecionado.nome = nome;
            produtoSelecionado.preco = preco;
            document.getElementById('modalNome').textContent = nome;
            document.getElementById('modalPreco').textContent = preco;
            document.getElementById('modalProduto').classList.add('aberto');
        }

        document.getElementById('modalFechar').addEventListener('click', () => {
            document.getElementById('modalProduto').classList.remove('aberto');
        });
        document.getElementById('modalProduto').addEventListener('click', function(e) {
            if (e.target === this) this.classList.remove('aberto');
        });
        document.getElementById('modalComprar').addEventListener('click', function() {
            const cor = document.getElementById('modalCor').value;
            const msg = `Olá! Gostaria de comprar:\nProduto: ${produtoSelecionado.nome}\nPreço: ${produtoSelecionado.preco}\nCor: ${cor}`;
            window.open('https://wa.me/5513992084636?text=' + encodeURIComponent(msg), '_blank');
            toast('📨 Mensagem enviada!', 'Sua solicitação foi enviada para o WhatsApp.');
        });

        // ================================================================
        // PESQUISA
        // ================================================================
        document.getElementById('btnPesquisa').addEventListener('click', pesquisarProdutos);
        document.getElementById('campoPesquisa').addEventListener('keyup', function(e) {
            if (e.key === 'Enter') pesquisarProdutos();
        });

        function pesquisarProdutos() {
            const termo = document.getElementById('campoPesquisa').value.toLowerCase().trim();
            if (!termo) { toast('🔍 Digite algo', 'Digite o nome de um produto para pesquisar.'); return; }
            navegar('produtos');
            setTimeout(() => {
                const cards = document.querySelectorAll('#gridTodosProdutos .card');
                let encontrou = false;
                cards.forEach(card => {
                    const nome = card.querySelector('.nome')?.innerText?.toLowerCase() || '';
                    const categoria = card.querySelector('.categoria-tag')?.innerText?.toLowerCase() || '';
                    if (nome.includes(termo) || categoria.includes(termo)) { card.style.display = 'block'; encontrou = true; }
                    else { card.style.display = 'none'; }
                });
                if (!encontrou) toast('🔍 Nenhum resultado', 'Tente outra palavra-chave.');
                else toast('🔍 Resultados encontrados', `Mostrando produtos com "${termo}"`);
            }, 100);
        }

        // ================================================================
        // FEEDBACK E AVALIAÇÃO
        // ================================================================
        document.getElementById('btnEnviarFeedback').addEventListener('click', function() {
            const nome = document.getElementById('feedbackNome').value.trim() || 'Anônimo';
            const texto = document.getElementById('feedbackTexto').value.trim();
            if (!texto) { toast('⚠️ Atenção', 'Por favor, escreva seu feedback.'); return; }
            feedbacks.push({ nome, texto });
            renderizarFeedbacks();
            document.getElementById('feedbackNome').value = '';
            document.getElementById('feedbackTexto').value = '';
            toast('📝 Feedback enviado!', 'Sua opinião é muito importante para nós.');
            adicionarNotificacao('📝 Novo feedback', `${nome} enviou um feedback.`, 'fa-regular fa-comment');
        });

        document.querySelectorAll('#ratingInput span').forEach(el => {
            el.addEventListener('click', function() {
                notaSelecionada = parseInt(this.getAttribute('data-nota'));
                document.querySelectorAll('#ratingInput span').forEach(e => {
                    const n = parseInt(e.getAttribute('data-nota'));
                    e.textContent = n <= notaSelecionada ? '★' : '☆';
                    e.style.color = n <= notaSelecionada ? '#ffb400' : '#333';
                });
            });
        });

        document.getElementById('btnEnviarAvaliacao').addEventListener('click', function() {
            const nome = document.getElementById('avaliacaoNome').value.trim() || 'Anônimo';
            const produto = document.getElementById('avaliacaoProduto').value.trim() || 'Produto não informado';
            const texto = document.getElementById('avaliacaoTexto').value.trim();
            const nota = notaSelecionada || 0;
            if (!texto) { toast('⚠️ Atenção', 'Por favor, escreva sua opinião.'); return; }
            if (nota === 0) { toast('⚠️ Atenção', 'Escolha uma nota de 1 a 5 estrelas.'); return; }
            const data = new Date().toLocaleDateString('pt-BR');
            avaliacoes.unshift({ nome, produto, nota, texto, data, curtidas: 0 });
            renderizarAvaliacoes();
            document.getElementById('avaliacaoNome').value = '';
            document.getElementById('avaliacaoProduto').value = '';
            document.getElementById('avaliacaoTexto').value = '';
            notaSelecionada = 0;
            document.querySelectorAll('#ratingInput span').forEach(e => {
                e.textContent = '☆';
                e.style.color = '#333';
            });
            toast('⭐ Avaliação enviada!', 'Obrigado por compartilhar sua opinião.');
            adicionarNotificacao('⭐ Nova avaliação', `${nome} avaliou a loja.`, 'fa-regular fa-star');
        });

        document.getElementById('btnCadastrar').addEventListener('click', cadastrarCliente);

        ['cadNome', 'cadEmail', 'cadTelefone'].forEach(id => {
            document.getElementById(id).addEventListener('keyup', function(e) {
                if (e.key === 'Enter') cadastrarCliente();
            });
        });

        window.addEventListener('scroll', function() {
            const btn = document.getElementById('backToTop');
            btn.classList.toggle('visible', window.scrollY > 500);
        });

        document.addEventListener('DOMContentLoaded', function() {
            renderizarProdutos(produtos.filter(p => p.destaque), 'gridDestaques');
            renderizarProdutos(produtos, 'gridTodosProdutos');
            renderizarAvaliacoes();
            renderizarFeedbacks();
            renderizarFavoritos();
            renderizarCarrinho();
            renderizarNotificacoes();
            renderizarCategoriasFull();
            initBanner();
            verificarConta();

            setTimeout(() => {
                adicionarNotificacao('👋 Bem-vinda!', 'Explore nossos produtos e aproveite as promoções.', 'fa-regular fa-hand-peace');
            }, 2000);
        });

        window.navegar = navegar;
        window.toggleFavorito = toggleFavorito;
        window.adicionarAoCarrinho = adicionarAoCarrinho;
        window.alterarQtdCarrinho = alterarQtdCarrinho;
        window.removerDoCarrinho = removerDoCarrinho;
        window.finalizarCompra = finalizarCompra;
        window.abrirModal = abrirModal;
        window.moverBanner = moverBanner;
        window.toast = toast;
        window.curtirAvaliacao = curtirAvaliacao;
        window.responderFeedback = responderFeedback;
        window.marcarNotificacaoLida = marcarNotificacaoLida;
        window.filtrarPorCategoria = filtrarPorCategoria;
        window.pesquisarProdutos = pesquisarProdutos;
        window.cadastrarCliente = cadastrarCliente;
        window.sairConta = sairConta;
        window.verificarConta = verificarConta;
        window.previewFoto = previewFoto;
        window.trocarFoto = trocarFoto;
        window.trocarFotoLogado = trocarFotoLogado;
        window.abrirDetalhesProduto = abrirDetalhesProduto;
        window.trocarImagemPrincipal = trocarImagemPrincipal;
        window.selecionarCor = selecionarCor;
        window.comprarDetalhes = comprarDetalhes;
        window.adicionarDetalhesAoCarrinho = adicionarDetalhesAoCarrinho;
        window.renderizarCarrossel = renderizarCarrossel;
    </script>
</body>
____________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________
# 💄 TC Beauty - Loja Virtual Premium

Loja virtual de maquiagem com visual luxuoso em preto e rosa, desenvolvida como projeto de TCC por duas adolescentes empreendedoras.

![Status](https://img.shields.io/badge/status-concluído-success)
![Versão](https://img.shields.io/badge/versão-1.0-FF1493)

---

## 📖 Sobre o Projeto

A **TC Beauty** é uma loja virtual completa desenvolvida em HTML, CSS e JavaScript puro, sem uso de frameworks. O projeto oferece uma experiência de compra premium para clientes que buscam produtos de maquiagem, com design elegante e funcionalidades práticas.

---

## ✨ Funcionalidades

- 🛍️ Catálogo com 30 produtos organizados por categoria
- 🛒 Carrinho de compras com cálculo automático
- ❤️ Sistema de favoritos
- 🔍 Pesquisa inteligente em tempo real
- 🔔 Sistema de notificações
- 👤 Cadastro de cliente com foto de perfil
- ⭐ Avaliações com estrelas e comentários
- 💬 Feedback com resposta do administrador
- 📱 Integração com WhatsApp para pedidos
- 📅 Integração com sistema de agendamento
- 📄 Páginas institucionais completas

---

## 🛠️ Tecnologias

- **HTML5** - Estrutura
- **CSS3** - Estilo e responsividade
- **JavaScript** - Interatividade
- **Font Awesome** - Ícones
- **Google Fonts** - Tipografia Poppins

---

## 🎨 Paleta de Cores

| Cor | Código | Uso |
|-----|--------|-----|
| Preto | `#000000` | Fundo principal |
| Rosa Pink | `#FF1493` | Cor de destaque |
| Rosa Claro | `#FFC0CB` | Detalhes |
| Branco | `#FFFFFF` | Textos |

---

## 📱 Responsividade

O site é 100% responsivo e funciona perfeitamente em:

- 📱 Celulares
- 📲 Tablets
- 💻 Computadores

---

## 🚀 Como Usar

1. Clone o repositório
2. Abra o arquivo `index.html` no navegador
3. Navegue pelas páginas e explore as funcionalidades

---

## 📁 Estrutura

tc-beauty/
├── index.html              # Site principal
├── agendamento.html        # Página de agendamento
├── imagens/                # Fotos dos produtos
└── README.md               # Documentação

---

## 🔮 Melhorias Futuras

- [ ] Banco de dados real
- [ ] Painel administrativo
- [ ] Autenticação segura
- [ ] Gateway de pagamento
- [ ] E-mails automáticos
- [ ] Cupons de desconto

---

## 👩‍💼 Autoria

Projeto desenvolvido por **duas adolescentes empreendedoras** apaixonadas por maquiagem, buscando mostrar que é possível criar uma loja virtual profissional com dedicação e estudo.

---

## 📞 Contato

- **WhatsApp:** (13) 99208-4636
- **E-mail:** 

---

⭐ Se este projeto te ajudou, deixe uma estrela no repositório!
