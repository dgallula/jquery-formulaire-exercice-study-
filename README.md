# jquery-formulaire-exercice-study-
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="utf-8" />
</head>
 <link href="style.css" rel="stylesheet" type="text/css" />
<body>
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
<script src="script.js"></script>
<h1>Accès utilisateur</h1>
<form id="form">
    <fieldset>
        <legend>Création de votre compte</legend>
        <label for="name">Nom d'utilisateur</label>
        <input type="text" name="name" id="name" class="js-hasHelpText" required placeholder="Saisissez votre nom">
        <label for="email">Adresse e-mail</label>
        <input type="text" name="email" id="email" class="js-hasHelpText" required placeholder="Saisissez votre email">
        <label for="password">Votre mot de passe</label>
        <input type="password" name="password" id="password" class="js-hasHelpText" required placeholder="Saisissez votre mot de passe">
        <label for="birthDate">Votre date de naissance</label>
        <input type="date" name="birthDate" id="birthDate" class="js-hasHelpText" required placeholder="Saisissez votre date de naissance">
        <label for="comment">Commentaire</label>
        <textarea name="comment" id="comment" class="js-hasHelpText" cols="30" rows="10"></textarea>
        <button type="submit">Soumettre le formulaire</button>
    </fieldset>
</form>
</body>
</html>

css 

    body {
        font-family: Calibri, serif;
    }
    form {
        max-width: 75%;
    }
    form label {
        display: block;
        font-weight: bold;
        margin-bottom: 10px;
    }
    fieldset {
        border: 1px solid lightgray;
        background-color: rgba(18, 2, 24, 0.25);
    }
    legend {
        font-style: italic;
        font-size: 1.1em;
        padding: 5px;
    }
    form input, form textarea {
        display: inline-block;
        margin-bottom: 10px;
        padding: 10px;
        width: 80%;
    }
    button[type=submit] {
        padding: 10px;
        margin-top: 15px;
        width: auto;
        display: block;
    }
    .help-text {
        color: #2b2b2b;
        
        js . 
        
    // Vous disposez d'un certain nombre de messages de contraintes propres à chaque élément du formulaire.

// 1 Dans un premier temps, associez ces contraintes à chacun des champs du formulaire. Vous pourriez vous aider du console.log présent dans le script de base. Par défaut, ces contraintes doivent être masquées. La contrainte concernée s'affichera uniquement lorsque l'utilisateur placera le focus sur ce champ, et disparaîtra s'il quitte le champ.Vous prendrez soin de les faire apparaître lentement.
//  Au chargement, les éléments h1 / legend seront masqués, puis lentement affichés sur 1000 ms. 
// Sur 2000 ms, la largeur du formulaire passera à 50 %.
$(document).ready(() => {
    let constraintsText = {
        name: 'Le nom d\'un utilisateur ne peut contenir plus de 20 caractères et ne doit contenir que des lettres.',
        email: 'Il doit s\'agir d\'un e-mail valide',
        password: 'Le mot de passe ne peut contenir que des chiffres et des lettres. Il doit disposer d\'au moins 6 caractères',
        birthDate: 'L\'utilisateur doit être une personne majeure',
        comment: 'Le commentaire ne peut excéder plus de 200 caractères'
    }
    $('.js-hasHelpText').each(function () {
        let helpText = '<p class="help-text">' + constraintsText[$(this).attr('name')] + '</p>'
        $(this).after(helpText)
    })
    let form = $('#form')
    form.animate({'width': '50%'}, 2000)
    $('h1, legend').hide().show(1000)
    form.on('focus', 'input, textarea', function () {
        $(this).next('.help-text').show('slow')
    })
    form.on('blur', 'input, textarea', function () {
        $('.help-text').hide()
    })
});           
