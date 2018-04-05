## <a name="sign-in-to-azure"></a>Iniciar sesión en Azure
Para crear el entorno de desarrollo, tenemos que iniciar sesión en Azure. Escriba el siguiente comando en una ventana de terminal:
```cmd
az login
```

> [!Note]
> Si no tiene una suscripción de Azure, puede crear una [cuenta gratuita](https://azure.microsoft.com/free).

### <a name="if-you-have-multiple-azure-subscriptions"></a>Si tiene varias suscripciones de Azure...
Ejecute lo siguiente para ver sus suscripciones: 
```cmd
az account list
```
Busque la suscripción que tenga `isDefault: true` en la salida JSON.
Si no es la suscripción que quiere usar, puede cambiar la suscripción predeterminada:
```cmd
az account set --subscription <subscription ID>
```
