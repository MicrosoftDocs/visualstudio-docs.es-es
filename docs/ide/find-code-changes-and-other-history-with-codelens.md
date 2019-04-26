---
title: Buscar cambios en el código y otro historial con CodeLens
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.CodeLens
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62ea3402a053ed57280ddbc946d79d27ab35f944
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62980893"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Buscar cambios en el código y otro historial con CodeLens

CodeLens le permite averiguar qué ocurrió con el código mientras sigue centrado en su trabajo sin dejar el editor. Puede buscar referencias de una parte del código, cambios de código, errores vinculados, elementos de trabajo, revisiones de código y pruebas unitarias.

::: moniker range=">=vs-2019"

> [!NOTE]
> Los indicadores de CodeLens del control de código fuente no están disponibles en la edición Visual Studio Community.

::: moniker-end

::: moniker range="vs-2017"

> [!NOTE]
> CodeLens solo está disponible en las ediciones Visual Studio Enterprise y Professional. No está disponible en la edición Visual Studio Community.

::: moniker-end

Vea dónde y cómo se usan las partes individuales del código de la solución:

![Indicadores CodeLens en el editor de código](../ide/media/codelens-overview.png)

Póngase en contacto con su equipo para informar de los cambios en el código sin salir del editor:

![CodeLens - Ponerse en contacto con su equipo](../ide/media/codelens-contact-info.png)

Para elegir qué indicadores desea ver, o para activar o desactivar CodeLens, vaya a **Herramientas** > **Opciones** > **Editor de texto** > **Todos los lenguajes** > **CodeLens**.

## <a name="find-references-to-your-code"></a>Buscar referencias al código

Puede buscar referencias en código de C# o de Visual Basic.

1. Elija el indicador **referencias** o presione **Alt**+**2**.

   ![Referencias de CodeLens](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > Si el indicador muestra **0 referencias**, significa que no tiene ninguna referencia de código de C# o Visual Basic. Pero podría haber referencias en otros elementos, como archivos *.xaml* y *.aspx*.

2. Para ver el código de referencia, mueva el mouse sobre la referencia en la lista.

   ![CodeLens - Leer referencia](../ide/media/codelens-peek-reference.png)

3. Para abrir el archivo que contiene la referencia, haga doble clic en la referencia.

### <a name="code-maps"></a>Mapas de código

Para ver las relaciones entre este código y sus referencias, [cree un mapa de código](../modeling/map-dependencies-across-your-solutions.md). En el menú contextual del mapa de código, seleccione **Mostrar todas las referencias**.

![CodeLens - Referencias en el mapa de código](../ide/media/codelensmappedreferences.png)

## <a name="find-changes-in-your-code"></a>Buscar cambios en el código

Inspeccione el historial del código para averiguar qué ocurrió. O bien, revise esos cambios antes de combinarlos con su código para saber cómo los cambios de otras bifurcaciones podrían afectarlo.

Es necesario:

- Edición Visual Studio Enterprise o Professional

- Azure DevOps Services, Team Foundation Server 2013 o posterior o Git

- [Skype Empresarial](/skypeforbusiness/) para ponerse en contacto con su equipo desde el editor de código.

Para el código de C# o Visual Basic que está almacenado con control de versiones de Team Foundation (TFVC) o Git, los detalles de CodeLens se obtienen en los niveles de clase y método (indicadores*code-element-level*). Si el repositorio Git está hospedado en TfGit, también obtendrá vínculos a elementos de trabajo TFS.

![Indicadores de nivel de elemento del código](../ide/media/codelens-element-level-indicators.png)

Para otros tipos de archivos que no son *.cs* o *.vb*, los detalles de CodeLens se obtienen para todo el archivo en un mismo lugar, en la parte inferior de la ventana (indicadores de *nivel de archivo*).

![Indicadores de nivel de archivo de CodeLens](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>Indicadores de nivel de elemento del código

Los indicadores de nivel de elemento de código permiten ver quién cambió el código y qué cambios se realizaron. Los indicadores de nivel de elemento de código están disponibles para el código de C# y Visual Basic.

Esto es lo que se ve cuando se usa el Control de versiones de Team Foundation (TFVC) en Team Foundation Server o Azure DevOps Services.

![CodeLens: Obtener el historial de cambios del código de TFVC](../ide/media/codelens-code-changes.png)

El período de tiempo predeterminado son los últimos 12 meses. Si el código se almacena en Team Foundation Server, puede cambiar el periodo de tiempo ejecutando el [comando TFSConfig](/tfs/server/ref/command-line/tfsconfig-cmd) junto con el [comando CodeIndex](../ide/codeindex-command.md) y la marca **/indexHistoryPeriod**.

Para ver un historial detallado de todos los cambios, incluidos los de hace más de un año, elija **Mostrar todos los cambios de archivo**:

![Mostrar todos los cambios de código](../ide/media/codelens-show-all-file-changes.png)

Se abre la ventana **Historial**:

![Ventana de historial para todos los cambios de código](../ide/media/codelenscodechangeshistory.png)

Esto es lo que se ve cuando los archivos están en un repositorio Git y se elige el indicador de cambios en el nivel de elemento de código:

![CodeLens: Obtener el historial de cambios del código de Git](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>Indicadores de nivel de archivo

Busque los cambios realizados en todo un archivo en los indicadores de nivel de archivo de la parte inferior de la ventana:

![CodeLens: Obtener detalles del archivo de código](../ide/media/codelens-file-level.png)

> [!NOTE]
> Los indicadores de nivel de archivo no están disponibles para los archivos de C# y Visual Basic.

Para obtener más detalles sobre un cambio, haga clic con el botón secundario en ese elemento. En función de si está usando TFVC o Git, hay diferentes opciones para comparar las versiones del archivo, ver detalles y realizar el seguimiento del conjunto de cambios, obtener la versión seleccionada del archivo y enviar un correo electrónico al autor del cambio. Algunos de estos detalles aparecen en **Team Explorer**.

También puede ver quién cambió el código a lo largo del tiempo. Esto puede ayudarle a identificar patrones en los cambios de su equipo y a evaluar su impacto.

![CodeLens: Ver el historial de cambios de código como un gráfico](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>Buscar cambios en la bifurcación actual

Su equipo puede tener varias ramas, por ejemplo, una rama Main y una rama Development secundaria, para reducir el riesgo de que el código estable se interrumpa.

![CodeLens: Buscar cuándo se bifurcó el código](../ide/media/codelensfirstbranchconceptual.png)

Puede saber cuántas personas realizaron cambios en el código y cuántos cambios se realizaron en la rama Main presionando **Alt**+**6**:

![CodeLens: Buscar número de cambios en su bifurcación](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>Buscar cuándo se bifurcó el código

Para buscar cuándo se bifurcó el código, navegue hasta el código de la rama secundaria. Después, seleccione el indicador **cambios** o presione **Alt**+**6**:

![CodeLens: Buscar cuándo se bifurcó el código](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>Buscar cambios entrantes de otras bifurcaciones

![CodeLens: Buscar cambios en el código en otras bifurcaciones](../ide/media/codelensbranchchangecheckinconceptual.png)

Puede ver los cambios entrantes. En la siguiente captura de pantalla, se realizó una corrección de errores en la rama "Dev":

![CodeLens: Cambiar comprobado en otra bifurcación](../ide/media/codelens-branch-changes-dev.png)

Puede revisar el cambio sin salir de la rama actual ("Main"):

![CodeLens: Ver cambio entrante desde otra bifurcación](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>Buscar cuándo se combinan los cambios

Puede ver cuándo se combinaron los cambios, para que pueda determinar qué cambios se incluyen en la rama:

![CodeLens - Cambios combinados entre bifurcaciones](../ide/media/codelensbranchmergedconceptual.png)

Por ejemplo, el código de la bifurcación Main ahora incluye la corrección de errores de la bifurcación "Dev":

![CodeLens - Cambios combinados entre bifurcaciones](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>Comparar un cambio entrante con la versión local

Compare un cambio entrante con la versión local presionando **MAYÚS**+**F10**, o haciendo doble clic en el conjunto de cambios.

![CodeLens: Comparar cambio entrante con local](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>Iconos de rama

El icono de la columna **Rama** indica cómo se relaciona la rama en la que está trabajando con la rama.

|**Iconos**|**El cambio provino de:**|
|--------------| - |
|![CodeLens: Cambiar desde icono de bifurcación actual](../ide/media/codelensbranchcurrenticon.png)|La bifurcación actual|
|![CodeLens: Cambiar desde icono de bifurcación primaria](../ide/media/codelensbranchparenticon.png)|La bifurcación primaria|
|![CodeLens: Cambiar desde icono de bifurcación secundaria](../ide/media/codelensbranchchildicon.png)|Una bifurcación secundaria|
|![CodeLens: Cambiar desde icono de bifurcación del mismo nivel](../ide/media/codelensbranchpeericon.png)|Una bifurcación del mismo nivel|
|![CodeLens: Cambiar desde icono de bifurcación alejada](../ide/media/codelensbranchfurtherawayicon.png)|Una bifurcación más alejada que una primaria, secundaria o del mismo nivel|
|![CodeLens: Combinar desde icono primario](../ide/media/codelensbranchmergefromparenticon.png)|Una combinación de la bifurcación primaria y una bifurcación secundaria|
|![CodeLens: Combinar desde icono de bifurcación secundaria](../ide/media/codelensbranchmergefromchildicon.png)|Una combinación de una bifurcación secundaria con la bifurcación secundaria|
|![CodeLens: Combinar desde icono de bifurcación no relacionada](../ide/media/codelensbranchmergefromunrelatedicon.png)|Una combinación de una bifurcación no relacionada (combinación sin base)|

## <a name="linked-work-items"></a>Elementos de trabajo vinculados.

Buscar elementos de trabajo vinculados seleccionando el indicador **elementos de trabajo** o presionando **Alt**+**8**.

![CodeLens - Buscar elementos de trabajo para código específico](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>Revisiones de código vinculadas

Buscar revisiones de código vinculadas seleccionando el indicador **revisiones**. Para usar el teclado, mantenga presionada la tecla **Alt** y, después, presione **Flecha izquierda** o **Flecha derecha** para navegar por las opciones de indicador.

![CodeLens - Ver solicitudes de revisión de código](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>Errores vinculados

Buscar errores vinculados seleccionando el indicador **errores** o presionando **Alt**+**7**.

![CodeLens - Buscar errores vinculados a conjuntos de cambios](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>Ponerse en contacto con el propietario de un elemento

Buscar el autor de un elemento seleccionando el indicador **autores** o presionando **Alt**+**5**.

![Ponerse en contacto con el propietario de un elemento](../ide/media/codelens-contact-item-owner.png)

Abra el menú contextual de un elemento para ver las opciones de contacto. Si tiene Lync o Skype Empresarial instalado, verá estas opciones:

![Opciones de contacto para un elemento](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>Pruebas unitarias asociadas

Puede buscar qué pruebas unitarias existen para el código de C# o Visual Basic sin tener que abrir el **Explorador de pruebas**.

1. Vaya al código de la aplicación que tenga [código pruebas unitarias](../test/unit-test-your-code.md) asociado.

2. Si todavía no lo ha hecho, compile la aplicación para que cargue los indicadores de prueba de CodeLens. Asegúrese de tener la [detección de ensamblados compilados](../test/test-explorer-faq.md#assembly-based-discovery) activada.

3. Revise las pruebas para el código presionando **Alt**+**3**.

     ![CodeLens - Elegir estado de la prueba en el editor de código](../ide/media/codelens-choose-test-indicator.png)

4. Si aparece un icono de advertencia ![icono de advertencia](../ide/media/codelenstestwarningicon.png), las pruebas todavía no se han ejecutado, así que ejecútelas.

     ![CodeLens - Ver pruebas unitarias no ejecutadas aún](../ide/media/codelens-tests-not-yet-run.png)

5. Para revisar la definición de una prueba, haga doble clic en el elemento de prueba en la ventana de indicador de CodeLens para abrir el archivo de código en el editor.

     ![CodeLens - Ir a la definición de la prueba unitaria](../ide/media/codelens-unit-test-definition.png)

6. Para revisar los resultados de la prueba, elija el indicador de estado de la misma (![icono de prueba no superada](../ide/media/codelenstestfailedicon.png) o ![icono de prueba superada](../ide/media/codelenstestpassedicon.png)) o presione **Alt**+**1**.

     ![CodeLens - Ver resultado de la prueba unitaria](../ide/media/codelens-unit-test-result.png)

7. Para ver cuántas personas cambiaron esta prueba, quién la cambió o cuántos cambios se realizaron, [busque el historial del código](#find-changes-in-your-code) y los elementos vinculados.

## <a name="keyboard-shortcuts"></a>Métodos abreviados de teclado

Para usar el teclado para seleccionar los indicadores, mantenga presionada la tecla **Alt** para mostrar las teclas numéricas relacionadas, luego presione el número que se corresponda con el indicador que quiere seleccionar.

![Números de acceso mediante el teclado](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> Para seleccionar el indicador **revisiones**, mantenga pulsada la tecla **Alt** mientras usa las teclas de flecha derecha e izquierda para navegar.

## <a name="q--a"></a>Preguntas y respuestas

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>P: ¿Cómo activo o desactivo CodeLens o elijo qué indicadores ver?

**R:**  Puede activar o desactivar los indicadores, excepto el de referencias. Vaya a **Herramientas** > **Opciones** > **Editor de texto** > **Todos los lenguajes** > **CodeLens**.

Cuando se activen los indicadores, también podrá abrir las opciones de CodeLens desde estos.

![CodeLens: Activar o desactivar los indicadores](../ide/media/codelensturnoffonindicatorsfromcode.png)

Active o desactive los indicadores de nivel de archivo de CodeLens con los iconos de botón de contenido adicional de la parte inferior de la ventana del editor.

![Activar o desactivar los indicadores de los archivos](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>P: ¿Dónde está CodeLens?

**R:** CodeLens aparece en el código de C# y Visual Basic, en el nivel de método, de clase, de indizador y de propiedad. CodeLens aparece en el nivel de archivo para todos los demás tipos de archivos.

- Asegúrese de que CodeLens esté activado. Vaya a **Herramientas** > **Opciones** > **Editor de texto** > **Todos los lenguajes** > **CodeLens**.

- Si el código está almacenado en TFS, asegúrese de que la indización de código esté activada. Para ello, use el [comando CodeIndex](../ide/codeindex-command.md) con el [comando TSF Config](/tfs/server/ref/command-line/tfsconfig-cmd).

- Los indicadores relacionados con DevOps aparecen solo cuando los elementos de trabajo se vinculan al código y cuando tiene permisos para abrir los elementos de trabajo vinculados. Confirme que tiene [permisos de miembro del equipo](/azure/devops/organizations/security/view-permissions?view=vsts).

- Los indicadores de pruebas unitarias no aparecen cuando el código de la aplicación no tiene pruebas unitarias. Dichos indicadores aparecen automáticamente en los proyectos de prueba. Si sabe que el código de la aplicación tiene pruebas unitarias, pero los indicadores de prueba no aparecen, pruebe a compilar la solución (**CTRL**+**Mayús**+**B**).

::: moniker range=">=vs-2019"

> [!TIP]
> Los indicadores del control de código fuente no están disponibles en la edición Visual Studio Community.

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> CodeLens no está disponible en la edición Visual Studio Community.

::: moniker-end

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>P: ¿Por qué no veo los detalles de los elementos de trabajo de una confirmación?

**R:** Esto podría deberse a que CodeLens no puede encontrar los elementos de trabajo en Azure Boards o TFS. Compruebe que está conectado al proyecto que tenga esos elementos de trabajo y que tiene permisos para verlos. Los detalles de elementos de trabajo también podrían no mostrarse si la descripción de confirmación tiene información incorrecta sobre los identificadores de elementos de trabajo en Azure Boards o TFS.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>P: ¿Por qué no veo los indicadores de Skype?

**R:** Los indicadores de Skype no aparecen si no ha iniciado sesión en Skype Empresarial, si no lo tiene instalado o si su configuración no es compatible. Pero podrá seguir enviando un correo electrónico:

![CodeLens - Ponerse en contacto con el propietario del conjunto de cambios por correo](../ide/media/codelenscodesendmailchangesetnolync1.png)

**¿Qué configuraciones de Skype y Lync se admiten?**

- Skype Empresarial (32 o 64 bits)

- Solo Lync 2010 o posterior (32 bits o 64 bits), pero no Lync Basic 2013 con Windows 8.1

CodeLens no admite tener instaladas distintas versiones de Lync o Skype. Puede que no estén localizadas para todas las versiones localizadas de Visual Studio.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>P: ¿Cómo se cambian la fuente y el color de CodeLens?

**R:** Vaya a **Herramientas** > **Opciones** > **Entorno** > **Fuentes y colores**.

![CodeLens - Cambiar la configuración de fuente y color](../ide/media/codelensoptionsfontscolorssettings.png)

Para usar el teclado:

1. Presione **Alt**+**T**+**O** para abrir el cuadro de diálogo **Opciones**.

2. Presione **Flecha arriba** o **Flecha abajo** para ir al nodo **Entorno** y, a continuación, presione **Flecha izquierda** para expandir el nodo.

3. Presione **Flecha abajo** para ir a **Fuentes y colores**.

4. Presione **TAB** para ir a la lista **Mostrar configuración para** y, a continuación, presione **Flecha abajo** para seleccionar **CodeLens**.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>P: ¿Se puede mover la pantalla de aviso de CodeLens?

**R:** Sí, elija ![Icono del Dock](../ide/media/codelensdockwindow.png) para acoplar CodeLens como ventana.

![Acoplar el botón en la ventana del indicador de CodeLens](../ide/media/codelensselectdockwindow.png)

![Ventana acoplada de referencias de CodeLens](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>P: ¿Cómo se actualizan los indicadores?

**R:** Eso depende del indicador:

- **Referencias**: Este indicador se actualiza automáticamente cuando cambia el código. Si el indicador **Referencias** está acoplado como una ventana independiente, actualice el indicador seleccionando **Actualizar**:

   ![Botón de actualización de referencias de CodeLens](../ide/media/codelensviewreferencesdocked.png)

- **Equipo**: Actualice estos indicadores al seleccionar **Actualizar indicadores de equipo CodeLens** desde el menú contextual:

   ![Elemento de menú Actualizar indicadores de equipo CodeLens](../ide/media/codelensrefreshindicatorsfromcode.png)

- **Prueba**: [Buscar pruebas unitarias para el código](#associated-unit-tests) para actualizar el indicador **Prueba**.

### <a name="q-whats-local-version"></a>P: ¿Qué es la "Versión local"?

**R:** La flecha **Versión local** apunta al conjunto de cambios más reciente de la versión local de un archivo. Cuando el servidor tiene conjuntos de cambios más recientes, estos aparecen encima o debajo de la flecha **Versión local** , según el orden usado para ordenar los conjuntos de cambios.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>P: ¿Puedo administrar la forma en que CodeLens procesa código para mostrar el historial y los elementos vinculados?

**R:** Sí. Si el código está en TFS, use el [comando CodeIndex](../ide/codeindex-command.md) con el comando [TSF Config](/tfs/server/ref/command-line/tfsconfig-cmd).

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>P: Los indicadores de prueba de CodeLens ya no aparecen en el archivo cuando abro la solución por primera vez. ¿Cómo puedo cargarlos?

**R:** Recompile el proyecto para obtener los indicadores de prueba de CodeLens que quiera cargar en el archivo. Asegúrese de tener la [detección de ensamblados compilados](../test/test-explorer-faq.md#assembly-based-discovery
) activada. Para mejorar el rendimiento, Visual Studio ya no obtiene la información de origen de los indicadores de prueba al cargar los archivos de código. Los indicadores de prueba se cargan después de la compilación o al desplazarse a una prueba haciendo doble clic en ella en el **Explorador de pruebas**.

## <a name="see-also"></a>Vea también

- [Características del editor de código](../ide/writing-code-in-the-code-and-text-editor.md)
