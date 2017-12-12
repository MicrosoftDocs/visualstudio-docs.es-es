---
title: 'Tutorial de Visual Studio Tools para Unity Azure: LeaderboardScene | Microsoft Docs'
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2127DEBA-9470-490B-BDDF-6F77A5ACC329
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: d257d1bdab02128d6c7ac8cebb819bc91ea8df41
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="leaderboardscene-explanation"></a>Explicación de LeaderboardScene

LeaderboardScene se compone únicamente de una interfaz de usuario. En la jerarquía Escena, **presione Alt y haga clic** en la **flecha para expandir** situada junto al GameObject Lienzo para expandirlo con sus GameObjects secundarios. Anidado debajo de Lienzo y Panel se encuentra el GameObject Leaderboard con el script Leaderboard adjuntado.

![GameObject Leaderboard](media/vstu_azure-leaderboard-explanation-image1.png)

## <a name="leaderboard-script"></a>Script Leaderboard

La clase `Leaderboard` usa una función `async Start`, a la que todavía se llama cuando se habilita el script, como si fuera una típica función `Start` de Unity.

`DownloadHighScoresAsync` usa las funciones `OrderBy` y `Take` de <a href="https://msdn.microsoft.com/en-us/library/azure/jj554257(v=azure.10).aspx">`IMobileServiceTable`</a> para ordenar las mejores puntuaciones de la tabla fácil de Azure y solo tomar las entradas principales según la constante `SizeOfHighScoreList`, que se almacenan en la lista `highScores`.

Después, se crea una instancia del recurso prefabricado de interfaz de usuario de la fila de mejores puntuaciones para cada entrada de la lista.

``` csharp
using Microsoft.WindowsAzure.MobileServices;
using System.Collections.Generic;
using System.Threading.Tasks;
using UnityEngine;
using System;
using UnityEngine.UI;

public class Leaderboard : MonoBehaviour
{
    [SerializeField]
    private GameObject rowPrefab;

    [SerializeField]
    private Text loadingText;

    public const int SizeOfHighScoreList = 10;
    private static int numberOfAttemptsToLoadData = 3;
    private static IMobileServiceTable<HighScoreInfo> highScoreTable_UseProperty;

    public static IMobileServiceTable<HighScoreInfo> HighScoreTable
    {
        get
        {
            if (highScoreTable_UseProperty == null)
            {
                highScoreTable_UseProperty = AzureMobileServiceClient.Client.GetTable<HighScoreInfo>();
            }

            return highScoreTable_UseProperty;
        }
    }

    public static async Task<List<HighScoreInfo>> GetTopHighScoresAsync()
    {
            return await DownloadHighScoresAsync(true);
    }

    private static async Task<List<HighScoreInfo>> DownloadHighScoresAsync(bool onlyTopEntries)
    {
        List<HighScoreInfo> highScoreList;

        Debug.Log("Downloading high score data from Azure...");

        for (int i = 0; i < numberOfAttemptsToLoadData; i++)
        {
            try
            {
                Debug.Log("Connecting... attempt " + (i + 1));

                if (onlyTopEntries)
                {
                    highScoreList = await HighScoreTable
                        .OrderBy(item => item.Time)
                        .Take(SizeOfHighScoreList)
                        .ToListAsync();
                }
                else
                {
                    highScoreList = await HighScoreTable.ToListAsync();
                }

                Debug.Log("Done downloading high score data.");
                return highScoreList;
            }
            catch (Exception e)
            {
                Debug.Log("Error connecting: " + e.Message);
            }

            if (i == numberOfAttemptsToLoadData - 1)
                Debug.Log("Connection failed. Check logs, try again later.");
            else
                await Task.Delay(500);
        }

        // If we can't successfully download a list from the server,
        // just make a new one to fail more gracefully.
        return highScoreList = new List<HighScoreInfo>();
    }

    private async void Start()
    {
        var highScores = await GetTopHighScoresAsync();

        if (highScores.Count == 0)
        {
            ShowEmptyLeaderboardMessage();
        }
        else
        {
            loadingText.gameObject.SetActive(false);

            foreach (var item in highScores)
            {
                var row = Instantiate(rowPrefab, this.transform).GetComponent<LeaderboardRow>();
                row.HighScoreInfo = item;
            }
        }
    }

    private void ShowEmptyLeaderboardMessage()
    {
        loadingText.text = "The leaderboard is empty!";
    }

    public static async Task DeleteAllEntriesAsync()
    {
       Debug.Log("Deleting leaderboard data...");

        var fullHighScoreList = await DownloadHighScoresAsync(false);

        foreach (var item in fullHighScoreList)
        {
            try
            {
                await HighScoreTable.DeleteAsync(item);
            }
            catch (Exception e)
            {
                Debug.Log("Error deleting leaderboard data: " + e.Message);
            }
        }
    }
}
```