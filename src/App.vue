<template>
  <div id="app" class="min-h-screen w-screen bg-gray-200 flex items-center justify-center">
    <div class="w-full max-w-md text-center">
    <p class="mb-2 text-gray-700 font-semibold font-sans tracking-wide">List 1</p>
      <draggable
        tag="ul"
        ghost-class="moving-card"
        class="w-full max-w-md"
        group="all-users"
        :list="users"
        :animation="200"
      >
        <user-card
          v-for="user in users"
          :user="user"
          :key="user.id"
          @edit="onEdit"
          @delete="onDelete"
        />
      </draggable>
    </div>
    <div class="w-full max-w-md ml-12 text-center">
    <p class="mb-2 text-gray-700 font-semibold font-sans tracking-wide">List 2</p>
    <draggable tag="ul"
               ghost-class="moving-card"
               group="all-users"
               :list="newUsers"
               :animation="200">
        <user-card v-for="user in newUsers"
                   :user="user"
                   :key="user.id"
                   @edit="onEdit"
                   @delete="onDelete">
        </user-card>
    </draggable>
</div>
  </div>
</template>

<script>
import "@/assets/css/tailwind.css";
import Draggable from "vuedraggable";
import UserCard from "@/components/UserCard";

export default {
  name: "app",
  components: {
    Draggable,
    "user-card": UserCard
  },
  data() {
    return {
      users: [
        {
          id: 1,
          name: "Adrian Schubert",
          avatar:
            "https://pickaface.net/gallery/avatar/unr_sample_161118_2054_ynlrg.png"
        },
        {
          id: 2,
          name: "Violet Gates",
          avatar: "https://pickaface.net/gallery/avatar/freud51c8b3f65e7dc.png"
        },
        {
          id: 3,
          name: "Steve Jobs",
          avatar: "https://pickaface.net/gallery/avatar/Opi51c74d0125fd4.png"
        },
        {
          id: 4,
          name: "Yassine Smith",
          avatar:
            "https://pickaface.net/gallery/avatar/unr_yassine_191124_2012_3gngr.png"
        },
        {
          id: 5,
          name: "Senior Saez",
          avatar:
            "https://pickaface.net/gallery/avatar/elmedinilla541c03412955c.png"
        }
      ],
      newUsers: [
        {
          id: 6,
          name: "Finley Rabins",
          avatar:
            "https://pickaface.net/gallery/avatar/48346295_191125_1628_ctsv.png"
        },
        {
          id: 7,
          name: "Coda Rabins",
          avatar:
            "https://pickaface.net/gallery/avatar/unr_kim1231_191121_1635_3d8er.png"
        },
        {
          id: 8,
          name: "Alyssa Rabins",
          avatar:
            "https://pickaface.net/gallery/avatar/unr_40225_191122_1302_9jl1l2.png"
        },
        {
          id: 7,
          name: "Nate Rabins",
          avatar:
            "https://pickaface.net/gallery/avatar/unr_chet_191122_1327_18kw.png"
        }
      ]
    };
  },
  methods: {
    onEdit(user) {
      alert(`Editing ${user.name}`);
    },
    onDelete(user) {
      alert(`Deleting ${user.name}`);
    }
  }
};
</script>

<style lang="scss" scoped>
.moving-card {
  @apply opacity-50 bg-gray-100 border border-blue-500;
}
</style>