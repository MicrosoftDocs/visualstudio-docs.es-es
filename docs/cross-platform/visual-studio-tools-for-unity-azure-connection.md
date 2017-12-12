---
title: "Tutorial de conexión de Visual Studio Tools para Unity Azure| Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 516A8FB2-8DFF-4BAB-8116-FDCD1C228DB3
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: f21e320fe9e27f6873b9caed3048a93bfa94a9c4
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="test-the-client-connection"></a>Prueba de la conexión de cliente

Ahora que se ha creado el singleton AzureMobileServiceClient, es el momento de probar la conexión de cliente.

## <a name="create-the-testclientconnection-script"></a>Crear el script TestClientConnection

1. En la carpeta **Scripts** de Unity, cree un script de C# denominado **TestClientConnection**.

2. Abra el script en Visual Studio, elimine el código de plantilla y agregue lo siguiente:

  ```csharp
  using System.Collections.Generic;
  using UnityEngine;
  using System.Threading.Tasks;
  using System;
  using System.Linq;
  using Microsoft.WindowsAzure.MobileServices;

  public class TestClientConnection : MonoBehaviour
  {
      void Start()
      {
          Task.Run(TestTableConnection);
      }

      private async Task TestTableConnection()
      {
          var table = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

          Debug.Log("Testing ToListAsync...");
          await TestToListAsync(table);

          Debug.Log("Testing InsertAsync...");
          await TestInsertAsync(table);

          Debug.Log("Testing DeleteAsync...");
          await TestDeleteAsync(table);

          Debug.Log("All testing complete.");
      }

      private async Task TestInsertAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await TestToListAsync(table);
              var initialCount = allEntries.Count();

              await table.InsertAsync(new CrashInfo { X = 1, Y = 2, Z = 3 });

              allEntries = await TestToListAsync(table);
              var newCount = allEntries.Count();

              Debug.Assert(newCount == initialCount + 1, "InsertAsync failed!");
          }
          catch (Exception)
          {
              throw;
          }
      }

      private async Task<List<CrashInfo>> TestToListAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await table.ToListAsync();
              Debug.Assert(allEntries != null, "ToListAsync failed!");
              return allEntries;
          }
          catch (Exception)
          {

              throw;
          }
      }

      private async Task TestDeleteAsync(IMobileServiceTable<CrashInfo> table)
      {
          var allEntries = await TestToListAsync(table);

          foreach (var item in allEntries)
          {
              try
              {
                  await table.DeleteAsync(item);
              }
              catch (Exception)
              {
                  throw;
              }
          }

          allEntries = await TestToListAsync(table);

          Debug.Assert(allEntries.Count() == 0, "DeleteAsync failed!");
      }
  }
  ```

3. En el menú **GameObject** de Unity, seleccione **GameObject > Crear vacío** para crear un objeto GameObject vacío de la escena de Unity. Cámbiele el nombre a **TestClientConnection**.

4. **Arrastre** el script TestClientConnection desde la ventana **Proyecto** de Unity al objeto GameObject TestClientConnection en la ventana **Jerarquía**.

5. En el menú de Unity, seleccione **Archivo > Save Scene as…** (Guardar escena como…). Asigne a la escena el nombre **Prueba de conexión de cliente** y haga clic en **Guardar**.

5. Haga clic en el botón **Reproducir** en Unity y observe la ventana Consola. Confirme que no se ha producido un error en ninguna de las aserciones.

6. Abra la tabla fácil InfoBloqueo en Azure Portal. Ahora debería tener una entrada con las coordenadas **X, Y, Z** **(1, 2, 3)** y el valor **true** en la columna **Eliminado**. Cada vez que ejecute la prueba, debería agregarse a la tabla una nueva entrada con los mismos valores pero un identificador único.

  ![Entrada de tabla fácil](media/vstu_azure-test-client-connection-image1.png)

## <a name="next-step"></a>Paso siguiente
* [Importación de los recursos de juego de muestra](visual-studio-tools-for-unity-azure-game-assets.md).
