<script>
    import Menu from '../../../../components/reader/menu.svelte'
    import SettingMenu from '../../../../components/reader/setting_menu.svelte';
    import Fileupload from '../../../../components/tool/fileupload.svelte';
</script>

<div class="navbar bg-neutral rounded-lg shadow-lg">
    <div class="flex-none">
        <!-- <button class="btn btn-square btn-ghost text-base-100"><i class="gg-menu-left-alt"></i></button> -->
        <Menu />
    </div>
    <div class="flex-1">
        <a class="btn btn-ghost normal-case text-xl text-base-100" href="/"
            >Novel Name</a
        >
    </div>
    <SettingMenu />
</div>


<Fileupload />

