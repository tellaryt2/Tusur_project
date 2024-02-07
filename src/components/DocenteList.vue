<script setup>
    import { ref } from 'vue';

    let isVariable = false;

    const dataListDocente = ref([
        {
            id: 1,
            fullName: "А. В. Демакова",
            image: "/img/docente-1.png"
        },
        {
            id: 2,
            fullName: "А. А. Квасникова",
            image: "/img/docente-2.png"
        },
        {
            id: 3,
            fullName: "А. А. Красина",
            image: "/img/docente-3.png"
        }
    ])

    const addNewDocente = () => {
        const newDocente = [
            {
                id: 4,
                fullName: "А. В. Демакова",
                image: "/img/docente-1.png"
            },
            {
                id: 5,
                fullName: "А. А. Квасникова",
                image: "/img/docente-2.png"
            },
            {
                id: 6,
                fullName: "А. А. Красина",
                image: "/img/docente-3.png"
            }
        ];
        newDocente.map(item => 
            dataListDocente.value.push(item)
        )
        isVariable = true;
    };

    const deleteNewDocente = () => {
        dataListDocente.value = dataListDocente.value.filter(
            docente => 
            docente.id !== 4 
            && docente.id !== 5 
            && docente.id !== 6
        );
        isVariable = false;
    }

    window.addEventListener('keydown', (event) => {
        if (event.key === 'Enter' && !isVariable) addNewDocente();
        else if (event.key === 'Enter' && isVariable) deleteNewDocente();
    });
</script>

<template>
    <div class="docente-list">
        <p>Преподаватели курса:</p>
        <ul class="docentes">
            <li v-for="docente in dataListDocente" :key="docente.id">
                <img :src="docente.image" alt="">
                <p><span>{{ docente.fullName }}</span></p>
            </li>
        </ul>
    </div>
</template>

<style>
.docente-list {
    display: flex;
    align-items: center;
    column-gap: 10px;
    
    padding-left: 40px;
    padding-right: 40px;
}

.docentes {
    display: flex;
    column-gap: 20px;

    flex-wrap: wrap;
    list-style-type: none;
    padding: 0;
}

.docente-list p {
    color: #2E3146;
    font-weight: 500;
    font-size: 16px;
    line-height: 1.4;
}

.docentes span {
    color: #71809B;
    font-weight: 500;
    font-size: 16px;
    line-height: 1.4;
    
}

.docentes li {
    display: flex;
    column-gap: 5px;
    align-items: center;
}

@media(max-width: 768px) {
    .docente-list {
        flex-direction: column;
    }

    .docente-list {
        align-items: flex-start;
    }

    .docente-list p {
        margin-bottom: 5px;
    }
    
    ul.docentes {
        margin-top: 5px;
    }

    .docentes {
        column-gap: 50px;
    }
}

@media(max-width: 550px) {
    .docentes {
        margin-top: 0px;
        padding-left: 0px;
    }
}

</style>