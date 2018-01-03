---
title: 'Tutorial de Visual Studio Tools para Unity Azure: HeatmapScene | Microsoft Docs'
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: E11DA08B-7341-4743-A817-0CAD59844305
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 472b6d5adae5e23007b9c1aa4d9c75118a94e1cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="heatmapscene-explanation"></a>Explicación de HeatmapScene

HeatmapScene contiene una instancia del recurso prefabricado **LevelGeometry**. De esta forma, las coordenadas de bloqueos que se cargan desde Azure se asignan correctamente a los gráficos del nivel.

## <a name="heatmap-script"></a>Script de mapa térmico

### <a name="initializecrashlistasync"></a>InitializeCrashListAsync
`InitializeCrashListAsync` se conecta a la tabla fácil CrashInfo en Azure y usa <a href="https://msdn.microsoft.com/en-us/library/azure/jj554274(v=azure.10).aspx">`ToListAsync`</a> para agregar todas sus entradas a una lista.

```
private async Task InitializeCrashListAsync()
 {
     Debug.Log("Downloading crash data from Azure...");

     for (int i = 0; i < numberOfAttempts; i++)
     {
         try
         {
             Debug.Log("Connecting... attempt " + (i +1));
             crashesFromServer = await crashesTable.ToListAsync();
             Debug.Log("Done downloading.");
             return;
         }
         catch (System.Exception e)
         {
             Debug.Log("Error connecting: " + e.Message);
         }

         if (i == numberOfAttempts - 1)
             Debug.Log("Connection failed. Check logs, try again later.");
         else
             await Task.Delay(500);
     }
 }
```

### <a name="spawnmarkersfromlist"></a>SpawnMarkersFromList
`SpawnMarkersFromList` recorre en iteración la lista de bloqueos recibida de Azure y crea una instancia de un recurso prefabricado de marcador de bloqueo para cada entrada.

```csharp
private void SpawnMarkersFromList()
{
    foreach (var item in crashesFromServer)
    {
        GameObject marker = GameObject.Instantiate(markerPrefab);
        marker.transform.position = new Vector3 { x = item.X, y = item.Y, z = item.Z };
    }
}
```

### <a name="deletecrashdataasync"></a>DeleteCrashDataAsync

`DeleteCrashDataAsync` se llama cuando el usuario presiona el botón **Borrar datos**. Recorre en iteración la lista local de bloqueos y llama a <a href="https://msdn.microsoft.com/en-us/library/azure/jj554258(v=azure.10).aspx">`DeleteAsync`</a> para cada entrada. Esto establece la columna **Eliminada** de cada entrada de la tabla fácil en **true**. `ToListAsync` ignora estas entradas eliminadas.

```csharp
public async void DeleteCrashDataAsync()
{
    Debug.Log("Deleting crash data...");
    foreach (var item in crashesFromServer)
    {
        try
        {
            await crashesTable.DeleteAsync(item);
        }
        catch (System.Exception e)
        {
            Debug.Log("Error deleting crash data: " + e.Message);
        }
        Debug.Log("Done deleting crash data.");
    }
    SceneManager.LoadScene(SceneManager.GetActiveScene().name);
}
```

## <a name="next-step"></a>Paso siguiente

* [Explicación de LeaderboardScene](visual-studio-tools-for-unity-azure-leaderboardscene.md)