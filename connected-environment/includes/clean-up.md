## <a name="clean-up"></a>Limpieza
Para eliminar por completo un Connected Environment en Azure (incluidos todos los servicios que hay ejecutándose en él), use el comando `vsce env rm`. Tenga en cuenta que esta acción es irreversible.

En el siguiente ejemplo se enumeran los Connected Environments existentes en la suscripción activa de Azure y, después, se elimina el entorno "myenv" que está en el grupo de recursos "myenv-rg".

```cmd
vsce env list
vsce env rm --name myenv --resource-group myenv-rg
```

