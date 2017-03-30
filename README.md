# Azure: Migrace zdroju do nové subscription
Migrace zdrojů v Azure mezi subscriptions
## Kdy je potřeba migrace
Když převádíte způsob placení, příklady:
* z PAYG do BizSpark, OPEN, EA
* z BizSpark do OPEN, EA
* z OPEN do EA

Popis toho, co lze migrovat přes portál a co je nutné migrovat přes support:
* https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-move-resources

Výtah z předchozího odkazu:
* obě předplatné Azure musí být pod stejným Active Directory tenantem
* pokud nejsou, můžete ho zkusit změnit
* aby jste to změnili, musíte být Service Administrátor

_"To attempt changing the directory, log in to the classic portal, and select Settings, and select the subscription. If the Edit Directory icon is available, select it to change the associated Active Directory."_

![změna tenantu](https://docs.microsoft.com/en-us/azure/azure-resource-manager/media/resource-group-move-resources/edit-directory.png)

_If that icon is not available, you must contact support to move the resources to a new tenant._

### Co můžete migrovat sami
* ARM (Azure Resource Manager) zdroje
* ASM (Classic) zdroje, kromě níže uvedených omezení

### Kdy musíte požádat support o migraci
* Pokud migrujete do jiného Active Directory tenantu
* pokud máte níže uvedená omezení na classic zdroje

* [Co můžete migrovat](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-move-resources#services-that-enable-move)
* [Co nemůžete migrovat](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-move-resources#services-that-do-not-enable-move)

## Omezeni migrace ASM prostředků přes portál
* všechny ASM zdroje musí být přesunuty zaráz
* cílová subscription nesmí obsahovat žádné ASM zdroje

## Migrace přes support request
* cílová subscription musí být prázdná
* vytvořte support request přes azure portál
* budete muset potvrdit vlastnictví subscription

## Nástroje:
[MigAz](https://github.com/Azure/migAz) - nástroj pro migraci z ASM do ARM nebo z AWS do Azure
