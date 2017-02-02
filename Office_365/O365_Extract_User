###########################
#### Extract User O365 ####
###########################

## Script pour extraire un Annuaire Office 365 en vue d'un Import vers un Active Directory Windows On-Premise

## Enregistrement d'un login / mdp "Admin"
$credential = Get-Credential

## Connexion à O365
Connect-MsolService -Credential $credential

## Vérification de la connexion à O365
Get-MsolUser -UserPrincipalName "fdesbiens@domain.com" | fl *
 
## Extract vers fichier "CSV"
Get-MsolUser | select  @{label="GivenName"; expression={$_.Firstname}}, 
                       @{label="sn"; expression={$_.Lastname}},
                       @{label="Name"; expression={$_.DisplayName}},
                       @{label="OfficePhone"; expression={$_.PhoneNumber}},
                       @{label="EmailAddress"; expression={$_.SignInName}},
                       @{label="StreetAddress"; expression={$_.StreetAddress}},
                       @{label="Country"; expression={$_.State}},
                       @{label="PostalCode"; expression={$_.PostalCode}},
                       @{label="Department"; expression={$_.Department}},
                       @{label="Fax"; expression={$_.Fax}},
                       @{label="MobilePhone"; expression={$_.MobilePhone}},
                       @{label="Title"; expression={$_.Title}},
                       @{label="ImmmutableID"; expression={$_.ImmutableId}},
                       @{label="UserPrincipalName"; expression={$_.UserPrincipalName}} | Export-Csv -Path "C:\Users\fdesbiens\Desktop\O365.csv" -Delimiter ";" -NoTypeInformation -Encoding UTF8
 
