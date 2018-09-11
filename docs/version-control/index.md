---
layout: LandingPage
title: Control de versiones en Visual Studio | VSTS y TFS
description: Guía de introducción al control de versiones en Visual Studio
keywords: VSTS, TFS, control de versiones
author: steved0x
ms.manager: douge
ms.author: sdanie
ms.date: 12/15/2017
ms.topic: landing-page
ms.prod: .net-core
ms.assetid: 2c119a5f-0272-48c0-8d6c-806196944aea
ms.workload:
- multiple
ms.openlocfilehash: e37645f8960aae54907dffeb0bcb88848d9cd63f
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44320584"
---
# <a name="version-control-in-visual-studio"></a>Control de versiones en Visual Studio

Los sistemas de control de versiones le ayudan a hacer el seguimiento de los cambios que se realizan en el código a lo largo del tiempo. A medida que hace algún cambio, el sistema de control de versiones toma una instantánea de los archivos. El sistema de control de versiones guarda la instantánea de manera permanente para que pueda recuperarla más adelante si es necesario. Visual Studio proporciona [Git](/azure/devops/repos/git/index?view=vsts) y [Control de versiones de Team Foundation (TFVC)](/azure/devops/repos/tfvc/index?view=vsts). Para decidir entre ambos sistemas, consulte el artículo sobre la [elección del control de versiones adecuado para el proyecto](/azure/devops/repos/tfvc/comparison-git-tfvc?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json).

## <a name="git"></a>Git
GIT es el sistema de control de versiones más usado actualmente y se está convirtiendo rápidamente en el estándar de control de versiones. GIT es un sistema de control de versiones distribuido, lo que significa que su copia local del código es un repositorio de control de versiones completo. Estos repositorios locales plenamente funcionales permiten trabajar sin conexión o de forma remota fácilmente. El trabajo se confirma localmente y, a continuación, se sincroniza la copia del repositorio con la del servidor. Este paradigma es distinto del control de versiones centralizado, donde los clientes deben sincronizar el código con un servidor antes de crear nuevas versiones.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="https://docs.microsoft.com/azure/devops/git/what-is-git">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Información sobre Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/share-your-code-in-git-vs-2017?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Introducción a Git con Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/clone?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Clonación de un repositorio de Git existente</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="tfvc"></a>TFVC

El control de versiones de Team Foundation (TFVC) es un sistema de control de versiones centralizado. Normalmente, los miembros del equipo solo tienen una versión de cada archivo en sus equipos de desarrollo. Los datos históricos se conservan únicamente en el servidor. Las bifurcaciones se basan en las rutas de acceso y se crean en el servidor.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/repos/tfvc/overview">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Información sobre TFVC</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Introducción a TFVC en Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
   <li>
        <a href="/azure/devops/repos/tfvc/get-code-reviewed-vs?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Revisión del código</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>


## <a name="resources"></a>Recursos

- [Guía de Git para profesionales](https://git-scm.com/book/en/v2)
- [Planeación de la migración a Git](https://docs.microsoft.com/azure/devops/git/centralized-to-git)
- [Migración de TFVC a Git](https://docs.microsoft.com/azure/devops/git/migrate-from-tfvc-to-git)