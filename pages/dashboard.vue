<template>
    <div>
        <NavBar />
        <div class="container">
            <table class="table table-striped">
                <tr>
                    <th>ID</th>
                    <th>User</th>
                    <th>Email</th>
                </tr>
                <tr>
                    <td>{{$auth.user.id}}</td>
                    <td>{{$auth.user.name}}</td>
                    <td>{{$auth.user.email}}</td>
                </tr>
            </table>
        </div>
    </div>
</template>