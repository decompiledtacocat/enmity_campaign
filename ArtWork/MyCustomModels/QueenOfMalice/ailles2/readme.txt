###########################################################################
README

Auteur : Clotaire

Date : 05/2003

Type de model : Arme [] | Equipement [x] | Unit� []

Source : http://www.metalplanet.org

Type d'animation: Birth []  | Death [] | Decay [] | Spell [] | Walk [] | Attack [] | Stand [] | Stand Victory []

Chemin du BLP : ailles2.mdx

MDL : Pr�sent [x] | Absent []

Commentaire : Aucun commentaire

############################################################################
                                  MODE D EMPLOIE

ARME OU EQUIPEMENT :

Si vous voulez attacher le model � une unit�, il suffi d'ajouter cette action : 

-action : Special Effect - Create Special Effect On Unit
		
	  Special Effect. Create a special effect attached to (Membre o� le model doit �tre attach�) of (NOM DE LA CIBLE) using (MODEL DU ZIP).mdx

------------------------------------------

UNITE :

Outils n�cessaires :
- UMS 3.6 ou sup�rieur
- Winmpq

Sous l'�diteur UMS :
	- Ouvrir l'�diteur d'unit�
	- Pour modifier le model de l'unit� choisit, il suffit de changer le chemin du MDX dans la ligne Model
	- Le chemin du nouveau MDX est arbitraire, il doit quand m�me partir du r�pertoire racine de Warcraft 3, 
		Exemple : Units\model\monmodel.mdx
	- Une fois ce changement fait, enregistrez la map.

Sous Winmpq :
	- Ouvrez la map derni�rement enregistr�e
	- D�placez simplement en faisant cliquer/glisser le MDX et le BLP correspondant au model
	- A ce moment Winmpq vous demandera un chemin, entrez le m�me chemin mis dans l'�diteur
		Gardons le m�me exemple : Units\model\
		NE METTEZ PAS LE NOM DU FICHIER DANS LE CHEMIN

#############################################################################

. : : http://www.metalplanet.org : : .
