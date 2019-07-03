library 'BanzaiCICD@develop'

banzai([
  appName: 'test-downstream-build',
  cleanWorkspace: [
    post: true
  ],
  stages: [
    [ name: 'build' ],
    [
      name: 'My Arbitrary Stage',
      steps: [
        /.*/: [
          [
            groovy: { logger "YO I RAN A GROOVY CLOSURE FROM A CUSTOM STAGE!" }
          ], 
          [
            shell: 'customStageScript.sh'
          ]
        ]
      ]
    ],
    [ name: 'publish' ],
    [ name: 'deploy' ]
  ],
  build: [
    /.*/: [:]
  ],
  publish: [
    /master/: [:]
  ],
  deploy: [
    /master/: [:]
  ],
  flowdock: [
    banzaiFlow: [
      credId: 'banzai-flowtoken',
      author: [
        name: 'Banzai',
        avatarUrl: 'https://static.greatbigcanvas.com/images/square/raygun/seafoam-wave,2033571.jpg?max=128',
        email: 'banzaicicd@gmail.com'
      ]
    ]
  ],
  email: [
    addresses: [
      banzai: 'banzaicicd@gmail.com'
    ],
    groups: [
      everyone: ['banzai'],
    ]
  ],
  notifications: [
    flowdock: [
      /.*/: [
        'banzaiFlow': ['.*']
      ]
    ],
    email: [
      /.*/: [
        groups: [
          'everyone': ['PIPELINE:(FAILURE|SUCCESS)']
        ],
        individuals: [
          'banzai': ['PIPELINE:PENDING']
        ]
      ]
    ]
  ]
])
