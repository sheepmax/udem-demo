# Newtondreams Demos

## First approach

This approach embeds the widgets directly into the HTML of the page. It follows the page flow and integrates naturally. Unfortunately it's difficult to have more than one widget included, and it comes with additional custom code to deal with the fact that we use `require.js`.

 <section>
    <div class="row">
        <div class="col-lg-5 controls">
            <div class="row">
                <div class="col">
                    <h4>Controles</h4>
                </div>
            </div> <!-- end .row- -->
            <div class="row">
                <div class="col">
                    <table class="table slider-table">
                        <tr>
                            <td nowrap>Densidad (&lambda;)</td>
                            <td class="w-100">
                                <div id="density_slider"></div>
                            </td>
                            <td><input id="density_label" type="text" class="input-80 form-control form-control-sm text-center" readonly></td>
                        </tr>
                    </table>
                </div>
            </div> <!-- end .row- -->
        </div>
        <div class="col-lg-7 mt-5 mt-lg-0" id="canvasContainer"></div>
    </div>
</section>

<link href="https://newtondreams.com/css/bootstrap.min.css" rel="stylesheet">
<link href="https://newtondreams.com/css/nouislider.css" rel="stylesheet">
<link href="https://newtondreams.com/css/index.css" rel="stylesheet">

<script>
    let MAIN = "https://newtondreams.com/fisica/barra_cargada/main.js";

    let JQUERY = "https://code.jquery.com/jquery-3.3.1.min.js";
    let NOUISLIDER = "https://newtondreams.com/js/nouislider.min.js";
    let BOOTSTRAPBUNDLE = "https://newtondreams.com/js/bootstrap.bundle.min.js";
    let APPBUNDLE = "https://newtondreams.com/js/core/dist/app.bundle.js";
    require.config({
        shim: {
            [NOUISLIDER]: {
                deps: [JQUERY]
            },
            [APPBUNDLE]:{
                deps: [NOUISLIDER]
            },
            [MAIN]: {
                deps: [APPBUNDLE]
            }
        }
    })
    require([NOUISLIDER], function(a){window.noUiSlider=a;})
    require([JQUERY, BOOTSTRAPBUNDLE, APPBUNDLE, MAIN])
</script>

## Second approach

The second approach uses iframes with some easy modifications to the source HTML:
1. The unnecessary sections of the body are removed, including the `<nav>` and `<footer>` tags.
2. All relative links are made absolute to the newtondreams website so we don't have to store things locally

The iframes size akwardly and can have scrollbars. This can be fixed with more sophisticated CSS.

<style>
    .resizeable-iframe {
        height: 500px;
        width: 100%;
        resize: both;
        overflow: auto;
        border: none;
    }
</style>
<iframe class="resizeable-iframe" src="plano_inclinado.html"></iframe>
<iframe class="resizeable-iframe" src="parabolico.html"></iframe>
