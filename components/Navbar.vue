<template>
    <nav>
        <b-navbar toggleable="lg" type="dark" variant="info">
            <b-navbar-brand href="/">Eduardo Mecchia</b-navbar-brand>

            <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

            <b-collapse id="nav-collapse" is-nav>
                <b-navbar-nav>
                    <b-nav-item href="/projects">Projects</b-nav-item>
                    <b-nav-item href="/certificates">Certificates</b-nav-item>
                    <b-nav-item href="/about">About</b-nav-item>
                </b-navbar-nav>

                <!-- Right aligned nav items -->
                <b-navbar-nav class="ml-auto">
                    <b-nav-item-dropdown text="Lang" right>
                        <b-dropdown-item href="#">EN</b-dropdown-item>
                        <b-dropdown-item href="#">IT</b-dropdown-item>
                    </b-nav-item-dropdown>
                </b-navbar-nav>
            </b-collapse>
        </b-navbar>
    </nav>
</template>