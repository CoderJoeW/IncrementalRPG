<template>
    <div class="modal fade" id="onLoadModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <button class="close" data-dismiss="modal" aria-hidden="true" onmousedown='return false;'>&times;</button>
                    <h4 class="modal-title" id="myModalLabel">Welcome to Incremental RPG!</h4>
                </div>
                <div class="modal-body">
                    <p>This is an open source project with the goal of creating the BEST incremental game in the world, ever!</p>
                    <p>Join in and help make this game awesome on <a href="https://github.com/samjb2/IncrementalRPG">GitHub</a>.</p>
                    <p>This box will show up everytime you start the game dont worry your progress stays saved we just havent added name saving yet but its coming!</p>
                    <h3>Name Your Town:</h3>
                    <input class="form-control" id="town" type="text">
                    <h3>Name Your Mayor:</h3>
                    <input class="form-control" id="mayor" type="text">
                </div>
                <div class="modal-footer">
                    <button id="modalClose" class="btn btn-success" data-dismiss="modal" onmousedown='return false;'>Done</button>
                </div>
            </div>
        </div>
    </div>
    <div class="row header">
        <div class="col-md-12">
            <h1>Incremental RPG
                <small id="version-number"></small>
            </h1>
        </div>
    </div>
    <div class="container">
        <div class="row">
            <div class="col-md-7">
                <div id="resources"></div>
            </div>
            <div class="col-md-5">
                <div class="row">
                    <div class="col-xs-6">
                        <div class="btn-group btn-group-justified">
                            <span class="btn btn-default disabled">Population</span>
                            <span id="population-total" class="btn btn-default disabled"></span>
                        </div>
                    </div>
                    <div class="col-xs-6">
                        <div class="btn-group btn-group-justified">
                            <span class="btn btn-default disabled">Max</span>
                            <span id="population-max" class="btn btn-default disabled"></span>
                        </div>
                    </div>
                </div>
                <div id="workers"></div>
            </div>
        </div>
        <div class="row">
            <div class="col-md-6">
                <hr>
                <div id="buildings"></div>
                <hr>
                <div id="storage-buttons"></div>
            </div>
            <div class="col-md-6">
                <hr>
                <div class="row" id="upgrade-two-axes">
                    <div class="col-xs-4">
                        <button id="twoAxes-name" class="btn btn-warning btn-block" onmousedown="clickIncrementUpgrade(resource.wood, 2, upgrades.twoAxes)"></button>
                    </div>
                    <div class="col-xs-8">
                        <h6>-<span id="twoAxes-wood-cost"></span> Wood | -<span id="twoAxes-stone-cost"></span> Stone | -<span id="twoAxes-meat-cost"></span> Meat</h6>
                        <h6 id="twoAxes-description"></h6>
                    </div>
                </div>
                <div class="row" id="upgrade-five-axes">
                    <div class="col-xs-4">
                        <button id="fiveAxes-name" class="btn btn-warning btn-block" onmousedown="clickIncrementUpgrade(resource.wood, 5, upgrades.fiveAxes)">Five Axes</button>
                    </div>
                    <div class="col-xs-8">
                        <h6>-<span id="fiveAxes-wood-cost"></span> Wood | -<span id="fiveAxes-stone-cost"></span> Stone | -<span id="fiveAxes-meat-cost"></span> Meat</h6>
                        <h6 id="fiveAxes-description"></h6>
                    </div>
                </div>
                <div class="row" id="upgrade-ten-axes">
                    <div class="col-xs-4">
                        <button id="tenAxes-name" class="btn btn-warning btn-block" onmousedown="clickIncrementUpgrade(resource.wood, 10, upgrades.tenAxes)">Ten Axes</button>
                    </div>
                    <div class="col-xs-8">
                        <h6>-<span id="tenAxes-wood-cost"></span> Wood | -<span id="tenAxes-stone-cost"></span> Stone | -<span id="tenAxes-meat-cost"></span> Meat</h6>
                        <h6 id="tenAxes-description"></h6>
                    </div>
                </div>
                <div class="row" id="upgrade-two-pickaxes">
                    <div class="col-xs-4">
                        <button id="twoPickaxes-name" class="btn btn-warning btn-block" onmousedown="clickIncrementUpgrade(resource.stone, 2, upgrades.twoPickaxes)"></button>
                    </div>
                    <div class="col-xs-8">
                        <h6>-<span id="twoPickaxes-wood-cost"></span> Wood | -<span id="twoPickaxes-stone-cost"></span> Stone | -<span id="twoPickaxes-meat-cost"></span> Meat</h6>
                        <h6 id="twoPickaxes-description"></h6>
                    </div>
                </div>
                <div class="row" id="upgrade-five-pickaxes">
                    <div class="col-xs-4">
                        <button id="fivePickaxes-name" class="btn btn-warning btn-block" onmousedown="clickIncrementUpgrade(resource.stone, 5, upgrades.fivePickaxes)">Five Axes</button>
                    </div>
                    <div class="col-xs-8">
                        <h6>-<span id="fivePickaxes-wood-cost"></span> Wood | -<span id="fivePickaxes-stone-cost"></span> Stone | -<span id="fivePickaxes-meat-cost"></span> Meat</h6>
                        <h6 id="fivePickaxes-description"></h6>
                    </div>
                </div>
                <div class="row" id="upgrade-ten-pickaxes">
                    <div class="col-xs-4">
                        <button id="tenPickaxes-name" class="btn btn-warning btn-block" onmousedown="clickIncrementUpgrade(resource.stone, 10, upgrades.tenPickaxes)">Ten Axes</button>
                    </div>
                    <div class="col-xs-8">
                        <h6>-<span id="tenPickaxes-wood-cost"></span> Wood | -<span id="tenPickaxes-stone-cost"></span> Stone | -<span id="tenPickaxes-meat-cost"></span> Meat</h6>
                        <h6 id="tenPickaxes-description"></h6>
                    </div>
                </div>
                <div class="row" id="upgrade-two-arrows">
                    <div class="col-xs-4">
                        <button id="twoArrows-name" class="btn btn-warning btn-block" onmousedown="clickIncrementUpgrade(resource.meat, 2, upgrades.twoArrows)"></button>
                    </div>
                    <div class="col-xs-8">
                        <h6>-<span id="twoArrows-wood-cost"></span> Wood | -<span id="twoArrows-stone-cost"></span> Stone | -<span id="twoArrows-meat-cost"></span> Meat</h6>
                        <h6 id="twoArrows-description"></h6>
                    </div>
                </div>
                <div class="row" id="upgrade-five-arrows">
                    <div class="col-xs-4">
                        <button id="fiveArrows-name" class="btn btn-warning btn-block" onmousedown="clickIncrementUpgrade(resource.meat, 5, upgrades.fiveArrows)">Five Axes</button>
                    </div>
                    <div class="col-xs-8">
                        <h6>-<span id="fiveArrows-wood-cost"></span> Wood | -<span id="fiveArrows-stone-cost"></span> Stone | -<span id="fiveArrows-meat-cost"></span> Meat</h6>
                        <h6 id="fiveArrows-description"></h6>
                    </div>
                </div>
                <div class="row" id="upgrade-ten-arrows">
                    <div class="col-xs-4">
                        <button id="tenArrows-name" class="btn btn-warning btn-block" onmousedown="clickIncrementUpgrade(resource.meat, 10, upgrades.tenArrows)">Ten Axes</button>
                    </div>
                    <div class="col-xs-8">
                        <h6>-<span id="tenArrows-wood-cost"></span> Wood | -<span id="tenArrows-stone-cost"></span> Stone | -<span id="tenArrows-meat-cost"></span> Meat</h6>
                        <h6 id="tenArrows-description"></h6>
                    </div>
                </div>
                <div class="row" id="upgrade-bigger-tents">
                    <div class="col-xs-4">
                        <button id="biggerTents-name" class="btn btn-warning btn-block" onmousedown="residentSizeUpgrade(buildings.tent, 3, upgrades.biggerTents)">Ten Axes</button>
                    </div>
                    <div class="col-xs-8">
                        <h6>-<span id="biggerTents-wood-cost"></span> Wood | -<span id="biggerTents-stone-cost"></span> Stone | -<span id="biggerTents-iron-cost"></span> Iron | -<span id="biggerTents-meat-cost"></span> Meat</h6>
                        <h6 id="biggerTents-description"></h6>
                    </div>
                </div>
            </div>
        </div>
        <div class="row">
            <div class="col-md-6">
                <hr>
                <div class="well">
                    <h3>Information</h3>
                    <div id="message-info" class="info"></div>
                </div>
            </div>
            <div class="col-md-6">
                <hr>
                <div class="well">
                    <h3>Upgrades</h3>
                    <div id="message-upgrades" class="info"></div>
                </div>
            </div>
        </div>
        <div class="row">
            <div class="col-md-12">
                <DevButtons :isDevMode="true"/>
            </div>
        </div>
    </div>
</template>

<script>
import DevButtons from '@/components/DevButtons.vue';

export default {
    name: 'Game',
    components: {
        DevButtons
    },
    methods: {

    }
}
</script>