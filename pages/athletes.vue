<template>
    <navigation/>
    <Listbox as="div" v-model="selected">
        <br>
        <ListboxLabel class="block text-sm font-medium leading-6 text-black container mx-auto">Select Athlete</ListboxLabel>
        <div class="relative mt-2 container mx-auto">
            <ListboxButton
                class="relative w-full cursor-default rounded-md bg-cyan-300 py-1.5 pl-3 pr-10 text-left text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus:outline-none focus:ring-2 focus:ring-indigo-500 sm:text-sm sm:leading-6">
                <span class="flex items-center">
                    <img :src="selected.avatar" alt="" class="h-5 w-5 flex-shrink-0 rounded-full" />
                    <span class="ml-3 block truncate">{{ selected.name }}</span>
                </span>
                <span class="pointer-events-none absolute inset-y-0 right-0 ml-3 flex items-center pr-2">
                    <ChevronUpDownIcon class="h-5 w-5 text-gray-400" aria-hidden="true" />
                </span>
            </ListboxButton>

            <transition leave-active-class="transition ease-in duration-100" leave-from-class="opacity-100"
                leave-to-class="opacity-0">
                <ListboxOptions
                    class="absolute z-10 mt-1 max-h-56 w-full overflow-auto rounded-md bg-white py-1 text-base shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none sm:text-sm">
                    <ListboxOption as="template" v-for="person in people" :key="person.id" :value="person"
                        v-slot="{ active, selected }">
                        <li
                            :class="[active ? 'bg-indigo-600 text-white' : 'text-gray-900', 'relative cursor-default select-none py-2 pl-3 pr-9']">
                            <div class="flex items-center">
                                <img :src="person.avatar" alt="" class="h-5 w-5 flex-shrink-0 rounded-full" />
                                <span :class="[selected ? 'font-semibold' : 'font-normal', 'ml-3 block truncate']">{{
                                    person.name }}</span>
                            </div>

                            <span v-if="selected"
                                :class="[active ? 'text-white' : 'text-indigo-600', 'absolute inset-y-0 right-0 flex items-center pr-4']">
                                <CheckIcon class="h-5 w-5" aria-hidden="true" />
                            </span>
                        </li>
                    </ListboxOption>
                </ListboxOptions>
            </transition>
        </div>
    </Listbox>
</template>
  
<script setup>
import { ref } from 'vue'
import { Listbox, ListboxButton, ListboxLabel, ListboxOption, ListboxOptions } from '@headlessui/vue'
import { CheckIcon, ChevronUpDownIcon } from '@heroicons/vue/20/solid'

const people = [
    {
        id: 1,
        name: 'Jethro Albay',
        avatar:
            'https://scontent.fcgy2-2.fna.fbcdn.net/v/t1.6435-9/67701755_1098319170367384_8176568256325222400_n.jpg?_nc_cat=103&ccb=1-7&_nc_sid=5f2048&_nc_eui2=AeG3epgD9lTbSXrLjWEQ3Qdmv-l5QMOifWC_6XlAw6J9YDiv8n0Zb04XGU2sKx5kefcn32rB7EPPbstUjd7wdUKM&_nc_ohc=5zqrgMOJolMQ7kNvgGwOMlo&_nc_ht=scontent.fcgy2-2.fna&oh=00_AYDaojbsUVWqrcWnvIxBKHO0bZiNSjmd_8cCOL11c0Eaig&oe=6665F2FF',
    },
    {
        id: 2,
        name: 'Max Verstappen',
        avatar:
            'https://scontent.fceb1-4.fna.fbcdn.net/v/t39.30808-6/428651294_928424001986561_3471882050230520714_n.jpg?_nc_cat=108&ccb=1-7&_nc_sid=5f2048&_nc_eui2=AeHCzIpvaYEOB2ji3e-tXzrOItcFVXvOdkci1wVVe852R2yKoUMYdwPKV62jZVsZzHWy01Q_Xyo67TondMx6XJpF&_nc_ohc=dxYQ7TExq6IQ7kNvgFwZXrz&_nc_ht=scontent.fceb1-4.fna&oh=00_AYAb10YKMLhDfBaG6JiuXJoC-PaakLfSNby_bUM-m9Ohkw&oe=6644FE57',
    },
    {
        id: 3,
        name: 'Lando Norris',
        avatar:
            'https://scontent.fcgy2-1.fna.fbcdn.net/v/t39.30808-6/424699341_955806369240124_8501182972811380766_n.jpg?_nc_cat=1&ccb=1-7&_nc_sid=5f2048&_nc_eui2=AeHdjP2ibIAi5u61j2t9ircMtQ8yA8c-oMu1DzIDxz6gyzIxskz-94X5DeLSaCf2HV95AFWciGuoa3J9ZU7CdpGz&_nc_ohc=i_vnWcZYxn8Q7kNvgEHcD2-&_nc_ht=scontent.fcgy2-1.fna&oh=00_AYAeOhaMq9rp4LKNgvulCm9L_gvuyzx1Hyk_SwtysfhzXw&oe=6644FA7F',
    },
    {
        id: 4,
        name: 'Charles Leclerc',
        avatar:
            'https://media.formula1.com/image/upload/f_auto,c_limit,q_75,w_1320/content/dam/fom-website/drivers/2024Drivers/leclerc',
    },
    {
        id: 5,
        name: 'Carlos Sainz Jr.',
        avatar:
            'https://scontent.fcgy2-2.fna.fbcdn.net/v/t1.6435-9/169372483_296213178539854_8682398326147906682_n.jpg?_nc_cat=104&ccb=1-7&_nc_sid=5f2048&_nc_eui2=AeFBV3sd-KXAPrCIURJqJcXdJLA9y-eAml0ksD3L54CaXVUmFk_7kwalw43OMsrKN1L-OmxVV6cCl7PK-awVJPcH&_nc_ohc=ITfJZPIUhhEQ7kNvgHrIfjE&_nc_ht=scontent.fcgy2-2.fna&oh=00_AYDZ5rEhneutEKCS4wbK9GZR51bGkAl_VqrAPO33cp6j4A&oe=6666A701',
    },
    {
        id: 6,
        name: 'Lewis Hamilton',
        avatar:
            'https://scontent.fcgy2-2.fna.fbcdn.net/v/t39.30808-6/278040289_529027711925601_3611808328967375187_n.jpg?_nc_cat=101&ccb=1-7&_nc_sid=5f2048&_nc_eui2=AeErEduu8e-0Q7Ry_f3eANLGUx_xnotQopJTH_Gei1CiktuYBOsr776Czj_uZJxZLJho0SCtv8JtKIs4Pyqoutaf&_nc_ohc=Y7WSAHcDw50Q7kNvgEyAvx1&_nc_ht=scontent.fcgy2-2.fna&oh=00_AYD1d_jZ3UR80D1c81YCNBKa3-YzdDO8LL5uf_czf4q_Dw&oe=6644EE58',
    },
    {
        id: 7,
        name: 'Daniel Ricciardo',
        avatar:
            'https://scontent.fceb1-4.fna.fbcdn.net/v/t39.30808-6/338020968_576043570959243_3482954723897804131_n.jpg?_nc_cat=107&ccb=1-7&_nc_sid=5f2048&_nc_eui2=AeGVjYXxvJSxZxPuVk_tlZC12v5ZjMTWFgfa_lmMxNYWB2DRE3TtiEzR0I9ChSqmirK5kO40pbUnEgkDyu0_vkWh&_nc_ohc=TPt0e1eMpWoQ7kNvgEoCBJj&_nc_ht=scontent.fceb1-4.fna&oh=00_AYABiJyN0eB7FFszyBcJJu649HfjJtw54lf9E2poIYzuVQ&oe=6644EE15',
    },
    {
        id: 8,
        name: 'Marc Marquez',
        avatar:
            'https://scontent.fceb1-3.fna.fbcdn.net/v/t39.30808-6/416100943_920657352750351_8776494571886432126_n.jpg?_nc_cat=106&ccb=1-7&_nc_sid=5f2048&_nc_eui2=AeH5AxTQm3LKb2mD4uPMl0aca95tmFdsi0Fr3m2YV2yLQb7-Phzh_uRQDA6FEfht0tdMs2OI4NS7CoVSGTn8JWjH&_nc_ohc=psv0gYnabF4Q7kNvgGEpnuQ&_nc_ht=scontent.fceb1-3.fna&oh=00_AYA24JCEai-yndqzBwLr0QfpUXJSPSwXC_yyqMh0DtBOIQ&oe=6644F2C9',
    },
    {
        id: 9,
        name: 'Fabio Quartararo',
        avatar:
            'https://upload.wikimedia.org/wikipedia/commons/1/13/Fabio_Quartararo_at_the_2022_San_Marino_Grand_Prix_at_Misano.jpg',
    },
    {
        id: 10,
        name: 'Stephen Curry',
        avatar:
            'https://scontent.fceb1-4.fna.fbcdn.net/v/t39.30808-6/317863527_703587747798089_1930520816525159219_n.jpg?_nc_cat=110&ccb=1-7&_nc_sid=5f2048&_nc_eui2=AeHk1rRgBE_-L03M5T2mnklpgdLxmWKEQq2B0vGZYoRCrd3hBZ1oZ7_NFL9eYI0kfqoTCoi0dyE8lqZaYI-KIh6n&_nc_ohc=XhafUCabDQkQ7kNvgFRZ7KW&_nc_ht=scontent.fceb1-4.fna&oh=00_AYB9dqHn6zYtTczEEQu8XIwVzQhQBPhTNTwMD-V4jZX_tQ&oe=66451023',
    },
]

const selected = ref(people[3])
</script>