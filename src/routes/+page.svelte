<script lang="ts" generics="TData">
import { AlignedGridsModule, AllCommunityModule, ModuleRegistry, createGrid, getGridApi,type Theme, themeQuartz, type GridOptions, type GridApi} from 'ag-grid-community'; 
import { onMount } from 'svelte';
ModuleRegistry.registerModules([AllCommunityModule]);


let showSkills = $state(true);
let showBoss = $state(false);
function toggleSkills() {
        showSkills = true
        showBoss = false
    }


function toggleBoss() {
        showBoss = true
        showSkills = false
    }

let divContainerEl: HTMLDivElement | undefined = $state();
let divContainerE2: HTMLDivElement | undefined = $state();
let api: GridApi<TData> | undefined = $state(undefined);
let api2: GridApi<TData> | undefined = $state(undefined);

    $effect(() => {
        api?.setGridOption("rowData", rowData);
        api2?.setGridOption("rowData", rowData);
    });
    onMount(() => {
        if(divContainerEl){
            api = createGrid(divContainerEl!, gridOptions);
        }
        if(divContainerE2){
            api2 = createGrid(divContainerE2!, gridOptions2);
        }
        return () => {
            api?.destroy();
            api2?.destroy();
        };
    });
const myTheme = themeQuartz
	.withParams({
        backgroundColor: "#26292F",
        browserColorScheme: "dark",
        cellTextColor: "#FFFF00",
        chromeBackgroundColor: "#000000",
        fontFamily: 'osrs',
        foregroundColor: "#FFF",
        headerFontSize: 20,
        fontSize: 16,
        oddRowBackgroundColor: "#000000"
    });
let rowData = $state<TData[]>([
    ]);

let failedData = $state<string[]>([
    ]);


let value = $state(``);
let templatePart1 = `<div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">`
let templatePart2 = `<span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`

let gridOptions: GridOptions = {
        columnDefs: [
        { field: 'Name'},
        {      
            headerName: '',
                headerComponentParams: { template: `
                <div class="ag-cell-label-container" role="presentation">
                    <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                    <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                    <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                        <img title="Total Level" src="/skills/overall.png"/>
                        <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>
                        `},
            field: "TotalLevel", sortable: true
        },
                {      
            headerName: '',
                headerComponentParams: { template: `
                <div class="ag-cell-label-container" role="presentation">
                    <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                    <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                    <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                        <img title="Attack" src="/skills/attack.png"/>
                        <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>
                        `
             },
            field: "Attack"
        },
                        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                        <img title="Defence" src="/skills/defence.png"/>
                        <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`
            },
            field: "Defence"
        },
                                {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Strength" src="/skills/strength.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`
            },
            field: "Strength"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Hitpoints" src="/skills/hitpoints.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Hitpoints"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Ranged" src="/skills/ranged.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Ranged"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Prayer" src="/skills/prayer.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Prayer"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Magic" src="/skills/magic.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Magic"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Cooking" src="/skills/cooking.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Cooking"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Woodcutting" src="/skills/woodcutting.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Woodcutting"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Fletching" src="/skills/fletching.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Fletching"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Fishing" src="/skills/fishing.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Fishing"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Firemaking" src="/skills/firemaking.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Firemaking"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Crafting" src="/skills/crafting.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Crafting"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Smithing" src="/skills/smithing.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Smithing"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Mining" src="/skills/mining.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Mining"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Herblore" src="/skills/herblore.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Herblore"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Agility" src="/skills/agility.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Agility"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Thieving" src="/skills/thieving.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Thieving"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Slayer" src="/skills/slayer.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Slayer"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Farming" src="/skills/farming.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Farming"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Runecraft" src="/skills/runecraft.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Runecraft"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Hunter" src="/skills/hunter.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Hunter"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Construction" src="/skills/construction.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Construction"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                    <div class="ag-cell-label-container" role="presentation">
                        <span data-ref="eMenu" class="ag-header-icon ag-header-cell-menu-button" aria-hidden="true"></span>
                        <span data-ref="eFilterButton" class="ag-header-icon ag-header-cell-filter-button" aria-hidden="true"></span>
                        <div data-ref="eLabel" class="ag-header-cell-label" role="presentation">
                                      <img title="Sailing" src="/skills/sailing.png"/>
                                                           <span data-ref="eText" class="ag-header-cell-text"></span>
                        <span data-ref="eFilter" class="ag-header-icon ag-header-label-icon ag-filter-icon" aria-hidden="true"></span>
                        <span data-ref="eSortOrder" class="ag-header-icon ag-header-label-icon ag-sort-order" aria-hidden="true"></span>
                        <span data-ref="eSortAsc" class="ag-header-icon ag-header-label-icon ag-sort-ascending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortDesc" class="ag-header-icon ag-header-label-icon ag-sort-descending-icon" aria-hidden="true"></span>
                        <span data-ref="eSortNone" class="ag-header-icon ag-header-label-icon ag-sort-none-icon" aria-hidden="true"></span>
                    </div>
                </div>`},
            field: "Sailing"
        }
        ],
        defaultColDef: {
        width: 100,
          },
        getRowId: (params) => params.data.Name,
        autoSizeStrategy: {
        type: 'fitCellContents',
        },
        rowData: rowData,
        theme: myTheme
    };
let gridOptions2: GridOptions = {
        columnDefs: [
        { field: 'Name'},
        {      
            headerName: '',
                headerComponentParams: { template: `
                        ${templatePart1}
                       <img title="Abyssal Sire" src="/sprites/abyssalSire.png"/>
                       ${templatePart2}`},
            field: "Abyssal Sire"
        },
        {      
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Alchemical Hydra" src="/sprites/alchemicalHydra.png"/>
                       ${templatePart2}`},
            field: "Hydra"
        },
        { 
            headerName: '',
            headerComponentParams: { template: `
                        ${templatePart1}
                                      <img title="Amoxliatl" src="/sprites/amoxliatl.png"/>
                       ${templatePart2}`},
            field: "Amoxliatl"
        },
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Araxxor" src="/sprites/araxxor.png"/>
                       ${templatePart2}`},
            field: "Araxxor"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Artio" src="/sprites/artioCallisto.png"/>
                       ${templatePart2}`},
            field: "Artio"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Barrows Chests" src="/sprites/barrows.png"/>
                       ${templatePart2}`},
            field: "Barrows Chests"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Bryophyta" src="/sprites/bryophyta.png"/>
                       ${templatePart2}`},
            field: "Bryophyta"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Callisto" src="/sprites/artioCallisto.png"/>
                       ${templatePart2}`},
            field: "Callisto"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Calvarion" src="/sprites/calVetion.png"/>
                       ${templatePart2}`},
            field: "Calvarion"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Cerberus" src="/sprites/cerberus.png"/>
                       ${templatePart2}`},
            field: "Cerberus"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Chambers of Xeric" src="/sprites/chambers.png"/>
                       ${templatePart2}`},
            field: "Chambers of Xeric"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Chambers of Xeric: Challenge Mode" src="/sprites/chambersHard.png"/>
                       ${templatePart2}`},
            field: "Chambers of Xeric: Challenge Mode"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Chaos Elemental" src="/sprites/chaosElemental.png"/>
                       ${templatePart2}`},
            field: "Chaos Elemental"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Chaos Fanatic" src="/sprites/chaosFanatic.png"/>
                       ${templatePart2}`},
            field: "Chaos Fanatic"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Commander Zilyana" src="/sprites/zilyana.png"/>
                       ${templatePart2}`},
            field: "Commander Zilyana"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Corporeal Beast" src="/sprites/corpBeast.png"/>
                       ${templatePart2}`},
            field: "Corporeal Beast"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Crazy Archaeologist" src="/sprites/crazyArch.png"/>
                       ${templatePart2}`},
            field: "Crazy Archaeologist"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Dagannoth Prime" src="/sprites/dagPrime.png"/>
                       ${templatePart2}`},
            field: "Dagannoth Prime"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Dagannoth Rex" src="/sprites/DagRex.png"/>
                       ${templatePart2}`},
            field: "Dagannoth Rex"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Dagannoth Supreme" src="/sprites/dagSupreme.png"/>
                       ${templatePart2}`},
            field: "Dagannoth Supreme"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Deranged Archaeologist" src="/sprites/derangedArch.png"/>
                       ${templatePart2}`},
            field: "Deranged Archaeologist"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Doom of Mokhaiotl" src="/sprites/mokha.png"/>
                       ${templatePart2}`},
            field: "Doom of Mokhaiotl"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Duke Sucellus" src="/sprites/dukeSucellus.png"/>
                       ${templatePart2}`},
            field: "Duke Sucellus"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="General Graardor" src="/sprites/graardor.png"/>
                       ${templatePart2}`},
            field: "General Graardor"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Giant Mole" src="/sprites/giantMole.png"/>
                       ${templatePart2}`},
            field: "Giant Mole"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Grotesque Guardians" src="/sprites/guardians.png"/>
                       ${templatePart2}`},
            field: "Grotesque Guardians"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Hespori" src="/sprites/hespori.png"/>
                       ${templatePart2}`},
            field: "Hespori"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Kalphite Queen" src="/sprites/kq.png"/>
                       ${templatePart2}`},
            field: "Kalphite Queen"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="King Black Dragon" src="/sprites/kbd.png"/>
                       ${templatePart2}`},
            field: "King Black Dragon"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Kraken" src="/sprites/kraken.png"/>
                       ${templatePart2}`},
            field: "Kraken"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="KreeArra" src="/sprites/kree.png"/>
                       ${templatePart2}`},
            field: "KreeArra"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Kril Tsutsaroth" src="/sprites/kril.png"/>
                       ${templatePart2}`},
            field: "Kril Tsutsaroth"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Moons" src="/sprites/moons.png"/>
                       ${templatePart2}`},
            field: "Lunar Chests"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Mimic" src="/sprites/mimic.png"/>
                       ${templatePart2}`},
            field: "Mimic"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Nex" src="/sprites/nex.png"/>
                       ${templatePart2}`},
            field: "Nex"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Nightmare" src="/sprites/nightmare.png"/>
                       ${templatePart2}`},
            field: "Nightmare"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Phosanis Nightmare" src="/sprites/nightmare.png"/>
                       ${templatePart2}`},
            field: "Phosanis Nightmare"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Obor" src="/sprites/obor.png"/>
                       ${templatePart2}`},
            field: "Obor"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Phantom Muspah" src="/sprites/muspah.png"/>
                       ${templatePart2}`},
            field: "Phantom Muspah"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Sarachnis" src="/sprites/sarachnis.png"/>
                       ${templatePart2}`},
            field: "Sarachnis"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Scorpia" src="/sprites/scorpia.png"/>
                       ${templatePart2}`},
            field: "Scorpia"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Scurrius" src="/sprites/scurrius.png"/>
                       ${templatePart2}`},
            field: "Scurrius"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Shellbane Gryphon" src="/sprites/shellbane.png"/>
                       ${templatePart2}`},
            field: "Shellbane Gryphon"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Skotizo" src="/sprites/skotizo.png"/>
                       ${templatePart2}`},
            field: "Skotizo"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Sol Heredit" src="/sprites/sol.png"/>
                       ${templatePart2}`},
            field: "Sol Heredit"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Spindel" src="/sprites/spindelVen.png"/>
                       ${templatePart2}`},
            field: "Spindel"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Tempoross" src="/sprites/tempoross.png"/>
                       ${templatePart2}`},
            field: "Tempoross"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="The Gauntlet" src="/sprites/gauntlet.png"/>
                       ${templatePart2}`},
            field: "The Gauntlet"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="The Corrupted Gauntlet" src="/sprites/cg.png"/>
                       ${templatePart2}`},
            field: "The Corrupted Gauntlet"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="The Hueycoatl" src="/sprites/huey.png"/>
                       ${templatePart2}`},
            field: "The Hueycoatl"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="The Leviathan" src="/sprites/leviathan.png"/>
                       ${templatePart2}`},
            field: "The Leviathan"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="The Royal Titans" src="/sprites/royalTitans.png"/>
                       ${templatePart2}`},
            field: "The Royal Titans"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="The Whisperer" src="/sprites/whisperer.png"/>
                       ${templatePart2}`},
            field: "The Whisperer"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Theatre of Blood" src="/sprites/tob.png"/>
                       ${templatePart2}`},
            field: "Theatre of Blood"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Theatre of Blood: Hard Mode" src="/sprites/tob.png"/>
                       ${templatePart2}`},
            field: "Theatre of Blood: Hard Mode"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Thermonuclear Smoke Devil" src="/sprites/thermy.png"/>
                       ${templatePart2}`},
            field: "Thermonuclear Smoke Devil"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Tombs of Amascut" src="/sprites/toa.png"/>
                       ${templatePart2}`},
            field: "Tombs of Amascut"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Tombs of Amascut: Expert Mode" src="/sprites/toaxpert.png"/>
                       ${templatePart2}`},
            field: "Tombs of Amascut: Expert Mode"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="TzKal-Zuk" src="/sprites/zuk.png"/>
                       ${templatePart2}`},
            field: "TzKal-Zuk"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="TzTok-Jad" src="/sprites/jad.png"/>
                       ${templatePart2}`},
            field: "TzTok-Jad"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Vardorvis" src="/sprites/vardorvis.png"/>
                       ${templatePart2}`},
            field: "Vardorvis"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Venenatis" src="/sprites/spindelVen.png"/>
                       ${templatePart2}`},
            field: "Venenatis"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Vetion" src="/sprites/calVetion.png"/>
                       ${templatePart2}`},
            field: "Vetion"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Vorkath" src="/sprites/vorkath.png"/>
                       ${templatePart2}`},
            field: "Vorkath"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Wintertodt" src="/sprites/wintertodt.png"/>
                       ${templatePart2}`},
            field: "Wintertodt"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Yama" src="/sprites/yama.png"/>
                       ${templatePart2}`},
            field: "Yama"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Zalcano" src="/sprites/zalcano.png"/>
                       ${templatePart2}`},
            field: "Zalcano"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Zulrah" src="/sprites/zulrah.png"/>
                       ${templatePart2}`},
            field: "Zulrah"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Colosseum Glory" src="/sprites/coloGlory.png"/>
                       ${templatePart2}`},
            field: "Colosseum Glory"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Grid Points" src="/sprites/collectionsLogged.png"/>
                       ${templatePart2}`},
            field: "Grid Points"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="League Points" src="/sprites/leaguePoints.png"/>
                       ${templatePart2}`},
            field: "League Points"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Deadman Points" src="/sprites/deadman.png"/>
                       ${templatePart2}`},
            field: "Deadman Points"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Bounty Hunter - Hunter" src="/sprites/BhHunter.png"/>
                       ${templatePart2}`},
            field: "Bounty Hunter - Hunter"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Bounty Hunter - Rogue" src="/sprites/BhRogue.png"/>
                       ${templatePart2}`},
            field: "Bounty Hunter - Rogue"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Bounty Hunter (Legacy) - Hunter" src="/sprites/BhHunter.png"/>
                       ${templatePart2}`},
            field: "Bounty Hunter (Legacy) - Hunter"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Bounty Hunter (Legacy) - Rogue" src="/sprites/BhRogue.png"/>
                       ${templatePart2}`},
            field: "Bounty Hunter (Legacy) - Rogue"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Clue Scrolls (all)" src="/sprites/ClueAll.png"/>
                       ${templatePart2}`},
            field: "Clue Scrolls (all)"},
        {            
             headerName: 'BEG',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Clue Scrolls (beginner)" src="/sprites/ClueAll.png"/>
                       ${templatePart2}`},
            field: "Clue Scrolls (beginner)"},
        {            
             headerName: 'EAS',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Clue Scrolls (easy)" src="/sprites/ClueAll.png"/>
                       ${templatePart2}`},
            field: "Clue Scrolls (easy)"},
        {            
             headerName: 'MED',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Clue Scrolls (medium)" src="/sprites/ClueAll.png"/>
                       ${templatePart2}`},
            field: "Clue Scrolls (medium)"},
        {            
             headerName: 'HAR',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Clue Scrolls (hard)" src="/sprites/ClueAll.png"/>
                       ${templatePart2}`},
            field: "Clue Scrolls (hard)"},
        {            
             headerName: 'ELI',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Clue Scrolls (elite)" src="/sprites/ClueAll.png"/>
                       ${templatePart2}`},
            field: "Clue Scrolls (elite)"},
        {            
             headerName: 'MAS',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Clue Scrolls (master)" src="/sprites/ClueAll.png"/>
                       ${templatePart2}`},
            field: "Clue Scrolls (master)"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="LMS - Rank" src="/sprites/LMS.png"/>
                       ${templatePart2}`},
            field: "LMS - Rank"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="PvP Arena - Rank" src="/sprites/pvpArena.png"/>
                       ${templatePart2}`},
            field: "PvP Arena - Rank"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Soul Wars Zeal" src="/sprites/soulWarsZeal.png"/>
                       ${templatePart2}`},
            field: "Soul Wars Zeal"},
        {             
            headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Rifts closed" src="/sprites/riftsClosed.png"/>
                       ${templatePart2}`},
            field: "Rifts closed"},
        {            
             headerName: '',
                headerComponentParams: { template: `
                  ${templatePart1}
                                      <img title="Collections Logged" src="/sprites/collectionsLogged.png"/>
                       ${templatePart2}`},
            field: "Collections Logged"
        }
        ],
        defaultColDef: {
        width: 100,
          },
        getRowId: (params) => params.data.Name,
        autoSizeStrategy: {
        type: 'fitCellContents',
        },
        rowData: rowData,
        theme: myTheme
    };
type Player = {
  "Name": string
  "TotalLevel": string
  "Attack": string
  "Defence": string
  "Strength": string
  "Hitpoints": string
  "Ranged": string
  "Prayer": string
  "Magic": string
  "Cooking": string
  "Woodcutting": string
  "Fletching": string
  "Fishing": string
  "Firemaking": string
  "Crafting": string
  "Smithing": string
  "Mining": string
  "Herblore": string
  "Agility": string
  "Thieving": string
  "Slayer": string
  "Farming": string
  "Runecraft": string
  "Hunter": string
  "Construction": string
  "Sailing": string
  "Grid Points": string
  "League Points": string
  "Deadman Points": string
  "Bounty Hunter - Hunter": string
  "Bounty Hunter - Rogue": string
  "Bounty Hunter (Legacy) - Hunter": string
  "Bounty Hunter (Legacy) - Rogue": string
  "Clue Scrolls (all)": string
  "Clue Scrolls (beginner)": string
  "Clue Scrolls (easy)": string
  "Clue Scrolls (medium)": string
  "Clue Scrolls (hard)": string
  "Clue Scrolls (elite)": string
  "Clue Scrolls (master)": string
  "LMS - Rank": string
  "PvP Arena - Rank": string
  "Soul Wars Zeal": string
  "Rifts closed": string
  "Colosseum Glory": string
  "Collections Logged": string
  "Abyssal Sire": string
  "Hydra": string
  "Amoxliatl": string
  "Araxxor": string
  "Artio": string
  "Barrows Chests": string
  "Bryophyta": string
  "Callisto": string
  "Calvarion": string
  "Cerberus": string
  "Chambers of Xeric": string
  "Chambers of Xeric: Challenge Mode": string
  "Chaos Elemental": string
  "Chaos Fanatic": string
  "Commander Zilyana": string
  "Corporeal Beast": string
  "Crazy Archaeologist": string
  "Dagannoth Prime": string
  "Dagannoth Rex": string
  "Dagannoth Supreme": string
  "Deranged Archaeologist": string
  "Doom of Mokhaiotl": string
  "Duke Sucellus": string
  "General Graardor": string
  "Giant Mole": string
  "Grotesque Guardians": string
  "Hespori": string
  "Kalphite Queen": string
  "King Black Dragon": string
  "Kraken": string
  "KreeArra": string
  "Kril Tsutsaroth": string
  "Lunar Chests": string
  "Mimic": string
  "Nex": string
  "Nightmare": string
  "Phosanis Nightmare": string
  "Obor": string
  "Phantom Muspah": string
  "Sarachnis": string
  "Scorpia": string
  "Scurrius": string
  "Shellbane Gryphon": string
  "Skotizo": string
  "Sol Heredit": string
  "Spindel": string
  "Tempoross": string
  "The Gauntlet": string
  "The Corrupted Gauntlet": string
  "The Hueycoatl": string
  "The Leviathan": string
  "The Royal Titans": string
  "The Whisperer": string
  "Theatre of Blood": string
  "Theatre of Blood: Hard Mode": string
  "Thermonuclear Smoke Devil": string
  "Tombs of Amascut": string
  "Tombs of Amascut: Expert Mode": string
  "TzKal-Zuk": string
  "TzTok-Jad": string
  "Vardorvis": string
  "Venenatis": string
  "Vetion": string
  "Vorkath": string
  "Wintertodt": string
  "Yama": string
  "Zalcano": string
  "Zulrah": string
}
        async function getOsrsPlayer(playerName: string) {
        console.log(value)
        const res = await fetch(`http://127.0.0.1:3000/api/player?name=${playerName}`);
         if(res.ok){
            const json = await res.json();
            return json;
         }
           throw(playerName);
        }

        async function getOsrsPlayers(){
            let splitString = value.split(",")
            for (const player of splitString) {
                try {
                    rowData.push(await getOsrsPlayer(player));
                } catch(e: any){
                    failedData.push(e);
                }

                console.log(failedData);
            }
        }
</script>


<div class="grid">
	<span class="margin">OSRS Player Bingo Stat Helper</span>
	<textarea placeholder="Input Players Names: Separate by ," bind:value></textarea>
    <button onclick={() => getOsrsPlayers()}>
    <span class="buttonText">Submit</span>
    </button>
    
{#if failedData.length > 0}    
    <div>
        <span class="marginbad">Failed Lookups:</span>
  
    {#each failedData as player}
    <span class="marginbad">{player},</span>
    {/each}
    </div>
{/if}
</div>
<div class="container">

<button onclick={() => toggleSkills()}>
    <span class="buttonText">Show Skills</span>
</button>
<button onclick={() => toggleBoss()}>
    <span class="buttonText">Show Boss</span>
</button>

</div>
<div class="outerbox">
    <div class="contents" class:active={showSkills}>
    <div style="height: 100%" bind:this={divContainerEl} class:active={showSkills} class='box'></div>
    </div>
    <div class="contents2" class:active={showBoss}>
    <div style="height: 100%" bind:this={divContainerE2} class:active={showBoss} class='box'></div>
    </div>
</div>


<style>
    .outerbox{
        display: grid;
    }
    .contents,.contents2{
         grid-row: 1;
         grid-column: 1;
    }
	.grid {
        display: flex;
        width: 100%;
        justify-content: space-evenly;
        flex-direction: column;
        align-items: center;
        height: 200px;
	}
    .contents.active{
         z-index: 10;
    }
     .contents2.active{
         z-index: 10;
    }
    .contents{
        z-index: 5;
    }
    .contents2{
        z-index: 5;
    }
    .margin{
        margin-bottom: 10px;
        color: #ffff00;
        font-size: 30px;
    }
    .marginbad{
        margin-bottom: 10px;
        color: #D2042D;
        font-size: 20px;
    }

	textarea {
		flex: 1;
        width: 100%;
        margin-bottom: 10px;
        height: 200px;
	}

    button {
        border: none;
        padding: 0.5rem 2rem;
        color: #ffff00;
        background-color: rgb(0,0,0);
        font-size: 1.5rem;
        border-radius: 1rem;
        transition: all 250ms;
        transform-origin: center;
        box-shadow: 0px 3px 3px rgba(0, 0, 0, 0.25),
        inset 0px -2px 3px rgba(0, 0, 0, 0.25);
        margin-bottom: 20px;
    }
    button:hover {
        cursor: pointer;
        transform: scale(0.975);
        box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.25);
        font-family: osrs;
    }
    .container{
        display: flex;
        width: 100%;
        justify-content: space-evenly;
    }
    .box.active{
        opacity: 1;
        z-index: 10;
    }
    .box{
    transition: opacity 0.3s ease;
    opacity: 0; /* Default opacity */
    z-index: 5;
    min-height: 600px;
    }
    .buttonText {
        font-family: osrs;

    }
</style>