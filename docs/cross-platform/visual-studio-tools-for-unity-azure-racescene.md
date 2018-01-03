---
title: 'Tutorial de Visual Studio Tools para Unity Azure: RaceScene | Microsoft Docs'
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1F9304E8-0F1B-4325-8BED-FE3EB0ADCE8D
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 7dc57628774624975cc6ede5bd241f322472bfe6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="racescene-explanation"></a>Explicación de RaceScene

RaceScene usa [recursos estándar](https://www.assetstore.unity3d.com/en/#!/content/32351) de Unity para crear el juego básico de carreras y el nivel. En esta sección, se explican los GameObjects relevantes y sus scripts en el orden en el que aparecen en la jerarquía RaceScene, como se muestra en la captura de pantalla siguiente.

![RaceScene](media/vstu_azure-racescene-explanation-image1.png)

## <a name="multipurposecamerarig"></a>MultipurposeCameraRig

**MultipurposeCameraRig** está tomado del paquete de recursos estándar de **cámaras**. Sus propiedades Inspector se han optimizado para seguir el coche a una velocidad adecuada.

## <a name="levelgeometry"></a>LevelGeometry

El recurso prefabricado LevelGeometry es un GameObject vacío que se usa para la organización. Sus GameObjects secundarios constituyen el espacio en el que se puede jugar. Todos los suelos, paredes, rampas y obstáculos se generan a partir de recursos prefabricados del paquete de recursos estándar de **creación de prototipos**.

Es **importante tener en cuenta** que, para que un objeto se pruebe para los choques que se registran en Azure, debe tener aplicada la etiqueta **Wall**.

![RaceScene](media/vstu_azure-racescene-explanation-image2.png)

## <a name="car"></a>Coche

El recurso prefabricado **Coche** está tomado del paquete de recursos estándar de **vehículos**. La única modificación que se ha realizado es la adición del componente de script **RecordCrashInfo**.

### <a name="recordcrashinfo"></a>RecordCrashInfo

Este script comprueba si se han producido choques en `OnCollisionEnter` y los registra en una lista. `crashRecordingCooldown` y `crashRecordingMinVelocity` limitan lo que en el juego se considera un choque para mantener un conjunto de datos relevante.

Cuando se produce el evento `RaceFinished`, `UploadNewCrashDataAsync` envía cada choque de la lista a la tabla fácil InfoChoque de Azure.

```Csharp
using System.Collections;
using System.Collections.Generic;
using System.Threading.Tasks;
using UnityEngine;

public class RecordCrashInfo : MonoBehaviour
{
    [Tooltip("Time in seconds after a crash before a new crash can be recorded.")]
    [SerializeField]
    private float crashRecordingCooldown = 1;

    [Tooltip("How fast car must be traveling before crash can be recorded.")]
    [SerializeField]
    private float crashRecordingMinVelocity = 8;

    [SerializeField]
    private Rigidbody carRigidbody;

    [SerializeField]
    private GameObject crashMarkerPrefab;

    [Tooltip("If turned on, crash markers spawn when the player crashes.")]
    [SerializeField]
    private bool spawnDebugMarkers = false;

    private bool isOnCooldown = false;
    private bool meetsMinVelocity = false;
    private bool isRaceFinished = false;

    private List<CrashInfo> newCrashes = new List<CrashInfo>();

    private void LateUpdate()
    {
        // We have to update this in LateUpdate as opposed to checking in OnCollisionEnter.
        // The car's velocity has already decreased from crashing by the time
        // OnCollisionEnter gets called.

        meetsMinVelocity = carRigidbody.velocity.magnitude >= crashRecordingMinVelocity;
    }

    private void OnCollisionEnter(Collision collision)
    {
        if (!isRaceFinished && collision.gameObject.tag == "Wall" && !isOnCooldown && meetsMinVelocity)
        {
            Debug.Log("Collided with wall!");

            newCrashes.Add(new CrashInfo
            {
                X = collision.transform.position.x,
                Y = collision.transform.position.y,
                Z = collision.transform.position.z
            });

            if (spawnDebugMarkers && Debug.isDebugBuild)
                Instantiate(crashMarkerPrefab, collision.transform.position, Quaternion.identity);

            isOnCooldown = true;
            StartCoroutine(Cooldown());
        }  
    }

    private IEnumerator Cooldown()
    {
        yield return new WaitForSeconds(crashRecordingCooldown);

        isOnCooldown = false;
    }

    private void OnRaceFinished()
    {
        Task.Run(UploadNewCrashDataAsync);
    }

    private async Task UploadNewCrashDataAsync()
    {
        var crashTable = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

        try
        {
            Debug.Log("Uploading crash data to Azure...");

            foreach (var item in newCrashes)
            {
                await crashTable.InsertAsync(item);
            }
            Debug.Log("Finished uploading crash data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading crash data: " + e.Message);
        }

    }

    private void OnEnable()
    {
        Checkpoint.RaceFinished += OnRaceFinished;
    }

    private void OnDisable()
    {
        Checkpoint.RaceFinished -= OnRaceFinished;
    }

}
```

## <a name="checkpoints"></a>Puntos de control

El nivel tiene cuatro GameObjects con el componente de script **Checkpoint**. Los puntos de control garantizan que el jugador no pueda acabar la carrera desplazándose en el sentido incorrecto por la pista. También detectan en qué momento el jugador acaba la carrera. Aquí es donde se invoca el evento `RaceFinished`.

## <a name="invisible-collision"></a>Colisión invisible

Se usan cubos primitivos estándar con los componentes MeshRenderer deshabilitados como colisión invisible para mantener al jugador dentro de los límites. Además, se aplica el material de física de **rebote** para garantizar que los coches que salen volando reboten correctamente contra las paredes invisibles y para evitar que el jugador golpee una pared invisible, se deslice por ella y acabe sobre una pared visible.

## <a name="recordhighscore"></a>RecordHighScore

Este script comprueba si el jugador ha obtenido una nueva puntuación máxima. En caso de que así sea, muestra el elemento `enterNamePopup`, que permite que el jugador escriba su nombre y haga clic en **Enviar**.

Una vez que se ha enviado el nombre de un jugador, se llama a `UploadNewHighScoreAsync` y se envía la nueva puntuación máxima a la tabla fácil HighScoreInfo de Azure.

```csharp
using System.Collections;
using System.Collections.Generic;
using Microsoft.WindowsAzure.MobileServices;
using UnityEngine;
using System.Threading.Tasks;
using System;
using System.Linq;
using UnityEngine.UI;

public class RecordHighScore : MonoBehaviour
{
    [SerializeField]
    private InputField nameInputField;

    [SerializeField]
    private CanvasGroup enterNamePopup;

    private List<HighScoreInfo> highScores;
    private string playerName = string.Empty;

    private async void Start()
    {
        ShowEnterNamePopup(false);
        highScores = await Leaderboard.GetTopHighScoresAsync();
    }

    private void ShowEnterNamePopup(bool shouldShow)
    {
        enterNamePopup.alpha = shouldShow ? 1 : 0;
        enterNamePopup.interactable = shouldShow;
    }

    public void SubmitButtonClicked()
    {
        playerName = nameInputField.text;
    }

    private async void OnAfterMostRecentScoreSet(float newScore)
    {
        bool isNewHighScore = CheckForNewHighScore(newScore);

        if (isNewHighScore)
        {
            Debug.Log("New High Score!");
            await GetPlayerNameAsync();
            await UploadNewHighScoreAsync(newScore);
        }
        else
        {
            Debug.Log("No new high score.");
        }
    }

    private async Task GetPlayerNameAsync()
    {
        // Wait a bit before showing the popup.
        // This just helps the player experience feel
        // less jarring.
        await Task.Delay(2000);
        ShowEnterNamePopup(true);

        // Wait until the player enters a name and clicks submit.
        // OnSubmitButtonClicked will set the playerName.
        while (playerName == string.Empty)
        {
            await Task.Delay(100);
        }

        ShowEnterNamePopup(false);
    }

    private bool CheckForNewHighScore(float newScore)
    {
        Debug.Log("Checking for a new high score...");

        bool isHighScoreListFull = highScores.Count >= Leaderboard.SizeOfHighScoreList;
        var lowerScores = highScores.Where(x => x.Time > newScore);

        return lowerScores.Count() > 0 || !isHighScoreListFull;
    }

    private async Task UploadNewHighScoreAsync(float newScore)
    {
        var newHighScoreInfo = new HighScoreInfo { Name = playerName, Time = newScore };

        try
        {
            Debug.Log("Uploading high score data to Azure...");

            await Leaderboard.HighScoreTable.InsertAsync(newHighScoreInfo);

            Debug.Log("Finished uploading high score data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading high score data: " + e.Message);
        }
    }

    private void OnEnable()
    {
        LapTimer.AfterMostRecentScoreSet += OnAfterMostRecentScoreSet;
    }

    private void OnDisable()
    {
        LapTimer.AfterMostRecentScoreSet -= OnAfterMostRecentScoreSet;
    }

}
```

## <a name="next-step"></a>Paso siguiente

* [Explicación de HeatmapScene](visual-studio-tools-for-unity-azure-heatmapscene.md)
