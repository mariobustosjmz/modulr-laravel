<template lang="html">
    <div class="panel panel-default">
        <div class="panel-body">
            <!-- User -->
            <div class="text-center">
                <img class="avatar-md" :src="user.avatar_url">
                <p class="lead">{{user.name}}</p>
                <small class="text-muted">{{user.email}}</small>
            </div>
        </div>
        <!-- Buttons -->
        <ul class="nav nav-pills nav-stacked">
            <li :class="{'active': activeLink == 'profile'}">
                <a :href="'/profile/'+user.id">
                    <i class="fa fa-fw fa-lg fa-user-circle-o" aria-hidden="true"></i> Profile
                </a>
            </li>
            <li :class="{'active': activeLink == 'work'}">
                <a :href="'/profile/'+user.id+'/work'">
                    <i class="fa fa-fw fa-lg fa-briefcase" aria-hidden="true"></i> Work
                </a>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                activeLink: '',
            }
        },
        props:['user'],
        mounted() {
            var str = window.location.pathname;
            var res = str.split("/");

            if (res.length == 3) {
                this.activeLink = res[1];
            } else if (res.length == 4) {
                this.activeLink = res[3];
            }
        }
    }
</script>
