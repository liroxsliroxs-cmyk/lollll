  window.CookieConsent.init({
    // More link URL on bar.
    modalMainTextMoreLink: "/contenido/politica-de-cookies/",
    // How long to wait until bar comes up.
    barTimeout: 1000,
    // Look and feel.
    theme: {
      barColor: '#333',
      barTextColor: '#FFF',
      barMainButtonColor: '#f3f3f3',
      barMainButtonTextColor: '#004488',
      modalMainButtonColor: '#004488',
      modalMainButtonTextColor: '#FFF',
    },
    language: {
      // Current language.
      current: 'es',
      locale: {
        es: {
          barMainText: 'Utilizamos cookies para mejorar tu experiencia en nuestra web. Al continuar navegando por la web aceptas nuestra política de cookies.',
          closeAriaLabel: 'cerrar',
          barLinkSetting: 'Configurar',
          barBtnAcceptAll: 'Aceptar todas',
          modalMainTitle: 'Configuración',
          modalMainText: 'Las cookies son pequeños fragmentos de datos enviados desde un sitio web y almacenados en la computadora del usuario por el navegador web del usuario mientras el usuario navega. Su navegador almacena cada mensaje en un pequeño archivo, llamado cookie. Cuando solicita otra página del servidor, su navegador envía la cookie de vuelta al servidor. Las cookies fueron diseñadas para ser un mecanismo confiable para que los sitios web recuerden información o registren la actividad de navegación del usuario.',
          modalBtnSave: 'Aceptar seleccionadas',
          modalBtnAcceptAll: 'Aceptar todo',
          modalAffectedSolutions: 'Cookies afectadas:',
          learnMore: ' Más información ',
          on: 'On',
          off: 'Off',
          enabled: 'Activadas.',
          disabled: 'Desactivadas.',
          checked: 'marcar',
          unchecked: 'desmarcar',
        }
      }
    },
    // List all the categories you want to display.
    categories: {
      // Unique name.
      // This probably will be the default category.
      necessary: {
        // The cookies here are necessary and category can't be turned off.
        // Wanted config value will be ignored.
        needed: true,
        // The cookies in this category will be let trough.
        // This probably should be false if category not necessary.
        wanted: true,
        // If checkbox is on or off at first run.
        checked: true,
        // Language settings for categories.
        language: {
          locale: {
            es: {
              name: 'Cookies necesarias',
              description: 'Las cookies necesarias ayudan a hacer una página web utilizable activando funciones básicas como la navegación en la página y el acceso a áreas seguras de la página web. La página web no puede funcionar adecuadamente sin estas cookies.',
            }
          }
        }
      },
	  estadisticas: {
		needed: false,
		wanted: false,
		checked: false,
		language: {
			locale: {
				es: {
					name: 'Analytics',
					description: 'Utilizada por Google Analitics para generar datos estadísticos acerca de cómo utiliza el visitante el sitio web.',
				  }
			  }
		  }
	  },
	  varias: {
		needed: false,
		wanted: false,
		checked: false,
		language: {
			locale: {
				es: {
					name: 'Varias',
					description: 'Se usan para ofrecer mejor experiencia en la navegación al usuario.',
				  }
			  }
		  }
	  }
    },
    // List actual services here.
    services: {
      // Unique name.
     
	  cconsent: {
        category: 'necessary',
        type: 'localcookie', // dynamic-script, script-tag, wrapped, localcookie
        search: 'cconsent',
        language: {
          locale: {
            es: {
              name: 'cconsent: Almacena el consentimiento del usuario para utilizar las cookies en el sitio web y las categorías seleccionadas.',
            }
          }
        }
      },
	  history: {
        category: 'varias',
        type: 'localcookie', // dynamic-script, script-tag, wrapped, localcookie
        search: 'history',
        language: {
          locale: {
            es: {
              name: 'history: Almacena las últimas páginas visitadas para ofrecerte una mayor comodidad de navegación.',
            }
          }
        }
      },
  
	  analytics: {
        // Existing category Unique name.
        // This example shows how to block Google Analytics.
        category: 'estadisticas',
        // Type of blocking to apply here.
        // This depends on the type of script we are trying to block.
        // Can be: dynamic-script, script-tag, wrapped, localcookie.
        type: 'dynamic-script',
        // Only needed if "type: dynamic-script".
        // The filter will look for this keyword in inserted scipt tags
        //  and block if match found.ok
        search: 'gtm',
        // List of known cookie names or regular expressions matching
        //  cookie names placed by this service.
        // These will be removed from current domain and .domain.
        cookies: [
          {
            // Known cookie name.
            name: '_gid',
            // Expected cookie domain.
            domain: '.${window.location.hostname}'
          },
		  {
            // Known cookie name.
            name: '_ga',
            // Expected cookie domain.
			 domain: '.${window.location.hostname}'
          },
          {
            // Regex matching cookie name.
            name: '/_ga*/'
          }
        ],
        language: {
          locale: {
            es: {
              name: 'Google Analytics'
            }
          }
        }
      }
	  
	  
    }
  });
