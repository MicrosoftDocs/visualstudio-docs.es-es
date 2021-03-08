---
ms.openlocfilehash: a33871a9a80dfcb6260f57e504c72ae2f72077bd
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101750881"
---
## <a name="prerequisites"></a>Requisitos previos

::: moniker range=">=vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) instalado con las cargas de trabajo adecuadas para el lenguaje elegido:
  * ASP.NET: **Desarrollo de ASP.NET y web**
  * Python: **Desarrollo de Python**
  * Node.js: **Desarrollo de Node.js**
::: moniker-end
::: moniker range="vs-2017"
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) instalado con las cargas de trabajo adecuadas para el lenguaje elegido:
  * ASP.NET: **Desarrollo de ASP.NET y web**
  * Python: **Desarrollo de Python**
  * Node.js: **Desarrollo de Node.js**
::: moniker-end

* Un proyecto de ASP.NET, ASP.NET Core, Python o Node.js. Si no dispone de un proyecto, seleccione una de las siguientes opciones:
  * ASP.NET Core: siga [Inicio rápido: Uso de Visual Studio para crear la primera aplicación web ASP.NET Core](../../ide/quickstart-aspnet-core.md)o use los pasos siguientes:
    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, elija **Crear un nuevo proyecto** en la ventana de inicio. Si la ventana de inicio no está abierta, elija **Archivo** > **Ventana de inicio**. Escriba **Aplicación web** en el cuadro de búsqueda, elija **C#** como lenguaje y, luego, seleccione **Aplicación web ASP.NET Core (Modelo-Vista-Controlador)** . Por último, elija **Siguiente**. En la siguiente pantalla, asigne el nombre **MyASPApp** al proyecto y luego elija **Siguiente**.

    Elija la plataforma de destino recomendada (.NET Core 3.1) o .NET 5 y, a continuación, elija **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En Visual Studio 2017, elija **Archivo**  >  **Nuevo proyecto**, seleccione **Visual C#**  >  **.NET Core** y después seleccione **Aplicación web ASP.NET Core**. Cuando se le solicite, seleccione la plantilla **Aplicación web (Modelo-Vista-Controlador)**, asegúrese de que la opción **Sin autenticación** está seleccionada y después elija **Aceptar**.
    ::: moniker-end
  * Python: siga [Inicio rápido: crear la primera aplicación web de Python con Visual Studio](../../ide/quickstart-python.md) o bien use **Archivo** > **Nuevo proyecto**, seleccione **Python** y después **Proyecto web de Flask**.
  * Node.js: siga [Inicio rápido: usar Visual Studio para crear su primera aplicación de Node.js](../../ide/quickstart-nodejs.md) o bien use **Archivo** > **Nuevo proyecto**, seleccione **JavaScript** y después **Aplicación web de Node.js en blanco**.

* Asegúrese de compilar el proyecto mediante el comando de menú **Compilar > Compilar solución** antes de seguir los pasos de implementación.