# Instruções de Deploy - Site Maçônico

## Opções de Hospedagem

### 1. Hospedagem Gratuita (Recomendada para Teste)

#### GitHub Pages
1. **Criar repositório no GitHub:**
   - Acesse github.com e crie uma conta (se não tiver)
   - Clique em "New repository"
   - Nome: `site-loja-maconica`
   - Marque como "Public"
   - Clique em "Create repository"

2. **Upload dos arquivos:**
   - Clique em "uploading an existing file"
   - Arraste todos os arquivos da pasta `site_maconico`
   - Commit com mensagem: "Site inicial da Loja Maçônica"

3. **Ativar GitHub Pages:**
   - Vá em Settings > Pages
   - Source: "Deploy from a branch"
   - Branch: "main"
   - Folder: "/ (root)"
   - Clique em "Save"

4. **Acessar o site:**
   - URL será: `https://seuusuario.github.io/site-loja-maconica`

#### Netlify
1. **Criar conta no Netlify:**
   - Acesse netlify.com
   - Crie uma conta gratuita

2. **Deploy por drag-and-drop:**
   - Na dashboard, arraste a pasta `site_maconico` para a área de deploy
   - Aguarde o processamento
   - Netlify gerará uma URL automática

3. **Personalizar domínio (opcional):**
   - Site settings > Domain management
   - Adicione um domínio personalizado

### 2. Hospedagem Paga (Recomendada para Produção)

#### Hostinger
1. **Contratar hospedagem:**
   - Plano Single ou Premium
   - Registrar domínio (ex: lojamaconica.com.br)

2. **Upload via FTP:**
   - Use FileZilla ou similar
   - Conecte com credenciais fornecidas
   - Upload para pasta `public_html`

#### HostGator
1. **Contratar plano de hospedagem**
2. **Usar cPanel para upload:**
   - File Manager > public_html
   - Upload e extrair arquivos

### 3. Hospedagem Especializada

#### Vercel
```bash
# Instalar Vercel CLI
npm i -g vercel

# Na pasta do projeto
vercel

# Seguir instruções na tela
```

#### Surge.sh
```bash
# Instalar Surge
npm install -g surge

# Na pasta do projeto
surge

# Escolher domínio e fazer deploy
```

## Configurações Necessárias

### 1. Personalização Obrigatória

Antes do deploy, edite os seguintes arquivos:

#### `index.html` - Informações da Loja
```html
<!-- Linha 6: Título da página -->
<title>Loja [NOME DA SUA LOJA] - Transforme sua vida através do conhecimento</title>

<!-- Linha 18: Nome da loja no header -->
<span class="logo-text">[NOME DA SUA LOJA]</span>

<!-- Seção de contato: Substitua os placeholders -->
<p>[Endereço completo da Loja]</p>
<p>[Telefone de contato]</p>
<p>[Email de contato]</p>
<p>[Horários de funcionamento]</p>
```

#### Seção "Nossa Loja" - Personalizar conteúdo
```html
<!-- Adicione informações específicas da sua loja -->
<p>Nossa Loja [NOME], fundada em [ANO], tem [X] anos de tradição...</p>
```

### 2. Configurações de SEO

#### Meta Tags (adicionar no `<head>`)
```html
<meta property="og:title" content="Loja [NOME] - Maçonaria">
<meta property="og:description" content="Junte-se à nossa loja maçônica...">
<meta property="og:image" content="https://seudominio.com/assets/images/esquadro_compasso_principal.jpg">
<meta property="og:url" content="https://seudominio.com">

<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Loja [NOME] - Maçonaria">
<meta name="twitter:description" content="Junte-se à nossa loja maçônica...">
```

### 3. Configurações de Analytics (Opcional)

#### Google Analytics
```html
<!-- Adicionar antes do </head> -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

## Configuração de Domínio

### 1. Registro de Domínio
Sugestões de nomes:
- `loja[nome].com.br`
- `[nome]maconica.com.br`
- `maconaria[cidade].com.br`

### 2. Configuração DNS
```
Tipo: A
Nome: @
Valor: [IP do servidor]

Tipo: CNAME
Nome: www
Valor: [dominio.com]
```

### 3. SSL/HTTPS
- A maioria dos provedores oferece SSL gratuito
- Certifique-se de que está ativado
- Redirecione HTTP para HTTPS

## Configuração de Email

### 1. Email Profissional
Configure emails como:
- `contato@sualojamaconcia.com.br`
- `secretario@sualojamaconcia.com.br`
- `veneravel@sualojamaconcia.com.br`

### 2. Formulário de Contato
O formulário atual é apenas frontend. Para funcionalidade completa:

#### Opção 1: Formspree (Gratuito)
```html
<!-- Alterar a tag form -->
<form action="https://formspree.io/f/SEU_ID" method="POST" class="contato-form">
```

#### Opção 2: Netlify Forms
```html
<!-- Adicionar atributo netlify -->
<form netlify class="contato-form" id="contato-form">
```

#### Opção 3: EmailJS
```javascript
// Adicionar no script.js
emailjs.send("service_id", "template_id", formData)
  .then(function(response) {
    alert('Mensagem enviada com sucesso!');
  });
```

## Manutenção e Atualizações

### 1. Backup Regular
- Faça backup dos arquivos mensalmente
- Mantenha cópias locais atualizadas
- Use controle de versão (Git)

### 2. Atualizações de Conteúdo
- Edite arquivos localmente
- Teste em ambiente local
- Faça upload das alterações

### 3. Monitoramento
- Configure Google Search Console
- Monitore velocidade com PageSpeed Insights
- Verifique funcionamento regularmente

## Checklist de Deploy

### Antes do Deploy
- [ ] Personalizar nome da loja
- [ ] Atualizar informações de contato
- [ ] Testar formulário de contato
- [ ] Verificar todas as imagens
- [ ] Testar responsividade
- [ ] Validar HTML/CSS

### Durante o Deploy
- [ ] Upload de todos os arquivos
- [ ] Verificar estrutura de pastas
- [ ] Testar carregamento do site
- [ ] Verificar links internos
- [ ] Testar formulários

### Após o Deploy
- [ ] Configurar SSL
- [ ] Submeter ao Google Search Console
- [ ] Configurar Analytics
- [ ] Testar em diferentes dispositivos
- [ ] Verificar velocidade de carregamento

## Solução de Problemas

### Site não carrega
1. Verificar se todos os arquivos foram enviados
2. Conferir estrutura de pastas
3. Verificar configurações DNS

### Imagens não aparecem
1. Verificar caminhos das imagens no HTML
2. Confirmar upload da pasta `assets/images`
3. Verificar permissões de arquivo

### Formulário não funciona
1. Configurar serviço de email (Formspree, etc.)
2. Verificar action do formulário
3. Testar validação JavaScript

### Site lento
1. Otimizar imagens (comprimir)
2. Minificar CSS/JavaScript
3. Usar CDN se necessário

## Suporte Técnico

Para problemas técnicos:
1. Consulte a documentação do provedor de hospedagem
2. Verifique logs de erro
3. Teste em ambiente local primeiro
4. Mantenha backups atualizados

---

**Que a Luz guie o sucesso de sua presença digital!**

