<draggable class="list-group" :list="item" group="people" @change="log">
          <div
            class="list-group-item"
            v-for="element in item"
            :key="element.name"
          >
            <Task :itemID="element.name" />
          </div>
        </draggable>




        list: [
        {
          section1: [
            { name: "John", id: 1 },
            { name: "Joao", id: 2 },
            { name: "Jean", id: 3 },
            { name: "Gerard", id: 4 },
          ],
        },
        {
          section2: [
            { name: "Juan", id: 5 },
            { name: "Edgard", id: 6 },
            { name: "Johnson", id: 7 },
          ],
        },
        { section3: [{ name: "Ahmet", id: 8 }] },
      ],
    };