<template>
    <div>
        <v-row id="tabs-row-desktop" align="center" justify="space-between">
            <v-col cols="12">
                <v-divider />
                <v-tabs v-model="selectedTab" class="mb-4">
                    <v-tab v-for="tab in tabs" :key="tab.id"">
                        <v-icon>{{ tab.icon }}</v-icon>
                        &nbsp&nbsp
                        <span>{{ tab.label }}</span>
                    </v-tab>
                </v-tabs>
                <v-item-group v-model="selectedTab">
                    <v-item v-for="tab in tabs" :key="tab.id">
                        <template #default="{ active }">
                            <v-card v-show="active" class="pa-4">
                                <h2>{{ tab.label }}</h2>
                                <p>{{ tab.content }}</p>
                            </v-card>
                        </template>
                    </v-item>
                </v-item-group>
            </v-col>
        </v-row>
    </div>
</template>

<script>
export default {
    name: "Tab",
    props: {
        photos: {
            type: Array,
            default: () => [],
            required: true
        },
        info: {
            type: Object,
            default: () => {},
            required: true
        }
    },
    data() {
        return {
            selectedTab: 0,
            tabs: [
                { id: 0, icon: "mdi-tag-outline", label: "Deals", content: "Deals Content" },
                { id: 1, icon: "mdi-grid", label: "Photos", content: this.photos },
                { id: 2, icon: "mdi-information-outline", label: "Info", content: this.info }
            ]
        };
    }
};
</script>
